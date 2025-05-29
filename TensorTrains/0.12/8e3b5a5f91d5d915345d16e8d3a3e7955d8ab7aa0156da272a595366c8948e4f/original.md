```
orthogonalize_left!(A::AbstractTensorTrain; svd_trunc::SVDTrunc)
```

Bring `A` to left-orthogonal form by means of SVD decompositions.

Optionally perform truncations by passing a `SVDTrunc`.
