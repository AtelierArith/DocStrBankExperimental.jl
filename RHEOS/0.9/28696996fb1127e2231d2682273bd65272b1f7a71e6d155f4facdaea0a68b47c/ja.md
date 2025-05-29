```
freezeparams(m::RheoModelClass, nt0::NamedTuple)
```

特定の値に凍結されたパラメータを持つ新しい `RheoModelClass` を返します

# 引数

  * `m`: 元の `RheoModelClass`
  * `nt0`: 各パラメータを凍結するための値を持つ名前付きタプル

# 例

```@example
julia> SLS2_mod = freezeparams( SLS2, (G₀=2,η₂=3.5))
[...]

julia> SLS2.G(1,[2,1,2,3,3.5])
3.8796492

julia> SLS2_mod.G(1,[1,2,3])
3.8796492
```
