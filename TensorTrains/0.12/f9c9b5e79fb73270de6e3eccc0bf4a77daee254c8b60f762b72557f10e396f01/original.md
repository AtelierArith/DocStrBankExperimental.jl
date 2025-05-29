```
orthogonalize_right!(A::AbstractTensorTrain; svd_trunc::SVDTrunc)
```

Bring `A` to right-orthogonal form by means of SVD decompositions.

Optionally perform truncations by passing a `SVDTrunc`.
