```
inner(M::CholeskySpace, p, X, Y)
```

[`CholeskySpace`](@ref) `M` における内積を、正の対角を持つ下三角行列 `p` と、任意の対角を持つ2つの接ベクトル `X`,`Y` で計算します。式は次のようになります。

$$
g_p(X,Y) = \sum_{i>j} X_{ij}Y_{ij} + \sum_{j=1}^m X_{ii}Y_{ii}p_{ii}^{-2}
$$
