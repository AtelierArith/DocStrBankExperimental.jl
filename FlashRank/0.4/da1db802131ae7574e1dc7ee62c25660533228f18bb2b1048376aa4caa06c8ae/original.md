```
RankerModel
```

A model for ranking passages, including the encoder and the ONNX session for inference.

For ranking, use as `rank(ranker, query, passages)` or as a functor `ranker(query, passages)`.
