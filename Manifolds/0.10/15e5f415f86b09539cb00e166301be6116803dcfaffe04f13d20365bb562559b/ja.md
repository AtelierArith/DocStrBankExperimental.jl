```
get_vector(::SymmetricPositiveDefinite, p, c, ::DefaultOrthonormalBasis)
```

[`get_basis`](@ref  get_basis(M::SymmetricPositiveDefinite,p,B::DefaultOrthonormalBasis{<:Any,ManifoldsBase.TangentSpaceType})からの基底を使用すると、このONBに関するベクトル再構成は次のように簡略化できます。

$$
   X = p^{\frac{1}{2}} \Biggl( \sum_{i=1,j=i}^n c_k \Delta_{i,j} \Biggr) p^{\frac{1}{2}}
$$

ここで、$k$は$i=1,\ldots,n, j=i,\ldots,n$の線形化されたインデックスです。
