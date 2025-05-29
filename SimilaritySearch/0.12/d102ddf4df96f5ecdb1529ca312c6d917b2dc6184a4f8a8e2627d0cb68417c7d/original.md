```
evaluate(::NormalizedCosineDistance, a, b)
```

Computes the cosine distance between two vectors, it expects normalized vectors. Please use NormalizedAngleDistance if you are expecting a metric function (cosine_distance is a faster alternative whenever the triangle inequality is not needed)
