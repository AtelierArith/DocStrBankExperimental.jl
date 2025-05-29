```
opex_var(stor_par::UnionOpexVar)
opex_var(stor_par::UnionOpexVar, t)
```

ストレージパラメータ `stor_par` のOPEX変数を `TimeProfile` として、または運用期間 `t` で返します。

!!! note "ストレージパラメータへのアクセス"
    [`Storage`](@ref) ノードの個々のストレージパラメータには、[`charge(n)`](@ref)、[`level(n)`](@ref)、および[`discharge(n)`](@ref) 関数を通じてアクセスできます。

