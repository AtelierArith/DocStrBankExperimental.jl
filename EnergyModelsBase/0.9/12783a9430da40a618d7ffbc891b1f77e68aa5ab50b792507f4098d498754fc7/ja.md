```
capacity(stor_par::AbstractStorageParameters)
capacity(stor_par::AbstractStorageParameters, t)
```

ストレージパラメータ `stor_par` の容量を `TimeProfile` として、または運用期間 `t` において返します。

!!! note "ストレージパラメータへのアクセス"
    [`Storage`](@ref) ノードの個々のストレージパラメータには、[`charge(n)`](@ref)、[`level(n)`](@ref)、および [`discharge(n)`](@ref) 関数を通じてアクセスできます。

