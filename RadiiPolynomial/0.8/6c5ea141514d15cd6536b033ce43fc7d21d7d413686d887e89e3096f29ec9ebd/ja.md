```
norm(a::AbstractSequence, p::Real=Inf)
```

`a`の`p`-ノルムを計算します。`p`は`1`、`2`、または`Inf`のいずれかでなければなりません。

これは次のように等価です：

  * `p == 1` の場合は `norm(a, Ell1(IdentityWeight()))`
  * `p == 2` の場合は `norm(a, Ell2(IdentityWeight()))`
  * `p == Inf` の場合は `norm(a, EllInf(IdentityWeight()))`

詳細は [`norm(::Sequence, ::BanachSpace)`](@ref) を参照してください。
