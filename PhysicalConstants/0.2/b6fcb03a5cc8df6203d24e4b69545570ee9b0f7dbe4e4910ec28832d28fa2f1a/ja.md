```
measurement(::PhysicalConstant{name,T,D,U}) where {T,D,U}
measurement(FloatType, ::PhysicalConstant{name,T,D,U}) where {T,D,U}
```

物理定数を標準不確かさを持つ `Quantity` として返します。浮動小数点精度は、デフォルトで `Float64` の `FloatType` でオプションとして指定できます。

```jldoctest
julia> using PhysicalConstants.CODATA2022, Measurements

julia> import PhysicalConstants.CODATA2022: μ_0

julia> μ_0
真空の磁気透過率 (μ_0)
値                           = 1.25663706127e-6 N A^-2
標準不確かさ                = 2.0e-16 N A^-2
相対標準不確かさ            = 1.6e-10
参照                         = CODATA 2022

julia> measurement(μ_0)
1.25663706127e-6 ± 2.0e-16 N A^-2

julia> measurement(Float32, μ_0)
1.256637e-6 ± 2.0e-16 N A^-2
```
