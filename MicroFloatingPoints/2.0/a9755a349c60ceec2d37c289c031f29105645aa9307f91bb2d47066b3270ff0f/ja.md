```
Emax(::Type{Floatmu{szE,szf}}) where {szE, szf}
```

`Floatmu{szE,szf}` の最大無偏指数を `UInt32` として返します。

参照: `exponent_max`, `exponent_raw_max`, [`Emin`](@ref)

# 例

```jldoctest
julia> Emax(Floatmu{8, 23})
0x0000007f
```
