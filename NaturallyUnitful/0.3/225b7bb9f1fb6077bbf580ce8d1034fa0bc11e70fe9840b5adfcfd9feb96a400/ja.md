```
unnatural(targetUnit, q)
```

量 `q` を `targetUnits` で指定された単位に変換し、変換を機能させるために必要な `ħ`、`c`、`ϵ₀` および `kb` の因子を自動的に挿入します。

例:

```
julia> unnatural(u"m", 5.067730759202785e6u"eV^-1")
1.0 m

julia> unnatural(u"m/s", 1)
2.99792458e8 m s^-1

julia> unnatural(u"K", 1u"eV")
11604.522060401006 K
```
