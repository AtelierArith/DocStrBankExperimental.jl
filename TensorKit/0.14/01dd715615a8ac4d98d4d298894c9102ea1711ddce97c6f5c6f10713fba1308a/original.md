```
InnerProductStyle(V::VectorSpace) -> ::InnerProductStyle
InnerProductStyle(S::Type{<:VectorSpace}) -> ::InnerProductStyle
```

Return the type of inner product for vector spaces, which can be either

  * `NoInnerProduct()`: no mapping from `dual(V)` to `conj(V)`, i.e. no metric
  * subtype of `HasInnerProduct`: a metric exists, but no further support is implemented.
  * `EuclideanInnerProduct()`: the metric is the identity, such that dual and conjugate spaces are isomorphic.
