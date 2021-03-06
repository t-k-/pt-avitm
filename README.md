# pt-avitm
[![Build Status](https://travis-ci.org/vlukiyanov/pt-avitm.svg?branch=master)](https://travis-ci.org/vlukiyanov/pt-avitm) [![codecov](https://codecov.io/gh/vlukiyanov/pt-avitm/branch/master/graph/badge.svg)](https://codecov.io/gh/vlukiyanov/pt-avitm)
[![Codacy Badge](https://api.codacy.com/project/badge/Grade/212b5a014c0a4399a9074b0db5b8ecbe)](https://www.codacy.com/app/vlukiyanov/pt-avitm?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=vlukiyanov/pt-avitm&amp;utm_campaign=Badge_Grade)

PyTorch implementation of a version of the Autoencoding Variational Inference For Topic Models (AVITM) algorithm. Compatible with PyTorch 1.0.0 and Python 3.6 or 3.7 with or without CUDA.

This follows (*or attempts to; note this implementation is unofficial*) the algorithm described in "Autoencoding Variational Inference For Topic Models" of Akash Srivastava, Charles Sutton (https://arxiv.org/abs/1703.01488).

## Examples

You can find a number of examples in the examples directory, see also Usage below.

## Usage

The simplest way to use the library is using the sklearn-compatible API, as below.

```python
import sklearn.datasets
from sklearn.feature_extraction.text import CountVectorizer
from sklearn.pipeline import make_pipeline

from ptavitm.sklearn_api import ProdLDATransformer

texts = sklearn.datasets.fetch_20newsgroups()['data']

pipeline = make_pipeline(
    CountVectorizer(
        stop_words='english',
        max_features=2500,
        max_df=0.9
    ),
    ProdLDATransformer()
)

pipeline.fit(texts)
result = pipeline.transform(texts)
```

## Other implementations of AVITM and similar

* Original TensorFlow: https://github.com/akashgit/autoencoding_vi_for_topic_models 
* PyTorch: https://github.com/hyqneuron/pytorch-avitm
