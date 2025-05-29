```
Emin(::Type{Floatmu{szE,szf}}) where {szE, szf}
```

`Floatmu{szE,szf}` の最小無偏指数を `Int32` として返します。

参照: `exponent_max`, `exponent_raw_max`, [`Emax`](@ref)

# 例

```jldoctest
julia> Emin(Floatmu{8, 23})
-126
```
