```
logdensityof(object, x)::Real
```

与えられた点 `x` における密度 `object`（またはその関連する密度）の対数値を計算します。

```jldoctest a
julia> DensityKind(object)
IsDensity()

julia> logy = logdensityof(object, x); logy isa Real
true
```

さらに [`DensityKind`](@ref) と [`densityof`](@ref) を参照してください。
