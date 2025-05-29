```
get_coordinates(::SymmetricPositiveDefinite, p, X, ::DefaultOrthonormalBasis)
```

[`get_basis`](@ref get_basis(M::SymmetricPositiveDefinite,p,B::DefaultOrthonormalBasis{<:Any,ManifoldsBase.TangentSpaceType})からの基底を使用すると、このONBに関する座標は次のように簡略化できます。

$$
   c_k = \mathrm{tr}(p^{-\frac{1}{2}}\Delta_{i,j} X)
$$

ここで、$k$は$i=1,\ldots,n, j=i,\ldots,n$の線形化されたインデックスです。
