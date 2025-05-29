```
opex_fixed(stor_par::UnionOpexFixed)
opex_fixed(stor_par::UnionOpexFixed, t_inv)
```

ストレージパラメータ `stor_par` の固定OPEXを `TimeProfile` として、または戦略的期間 `t_inv` で返します。

!!! note "ストレージパラメータへのアクセス"
    [`Storage`](@ref) ノードの個々のストレージパラメータには、[`charge(n)`](@ref)、[`level(n)`](@ref)、および [`discharge(n)`](@ref) 関数を通じてアクセスできます。

