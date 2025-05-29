```
opnorm(A::LinearOperator, p::Real=Inf)
```

`A`の演算子ノルムを`p`-ノルムによって計算します。`p`は`1`、`2`または`Inf`のいずれかである必要があります。

これは次のように等価です：

  * `opnorm(A, Ell1(IdentityWeight()))` もし `p == 1` の場合
  * `opnorm(A, Ell2(IdentityWeight()))` もし `p == 2` の場合
  * `opnorm(A, EllInf(IdentityWeight()))` もし `p == Inf` の場合

参照：[`opnorm(::LinearOperator, ::BanachSpace)`](@ref)、[`opnorm(::LinearOperator, ::BanachSpace, ::BanachSpace)`](@ref) および [`opnorm(::LinearOperator{<:VectorSpace,ParameterSpace}, ::BanachSpace)`](@ref)。
