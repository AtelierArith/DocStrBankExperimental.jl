```
inner(M::CholeskySpace, p, X, Y)
```

Compute the inner product on the [`CholeskySpace`](@ref) `M` at the lower triangular matrix with positive diagonal `p` and the two tangent vectors `X`,`Y`, i.e they are both lower triangular matrices with arbitrary diagonal. The formula reads

$$
g_p(X,Y) = \sum_{i>j} X_{ij}Y_{ij} + \sum_{j=1}^m X_{ii}Y_{ii}p_{ii}^{-2}
$$
