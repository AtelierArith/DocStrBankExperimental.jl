```
densityof(object, x)::Real
```

与えられた点 `x` における密度 `object`（またはその関連する密度）の値を計算します。

```jldoctest a
julia> DensityKind(object)
IsDensity()

julia> densityof(object, x) == exp(logdensityof(object, x))
true
```

`densityof(object, x)` は `exp(logdensityof(object, x))` にデフォルト設定されていますが、特化されることがあります。

[`DensityKind`](@ref) および [`densityof`](@ref) も参照してください。
