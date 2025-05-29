```
measurement(::PhysicalConstant{name,T,D,U}) where {T,D,U}
measurement(FloatType, ::PhysicalConstant{name,T,D,U}) where {T,D,U}
```

Return the physical constant as a `Quantity` with standard uncertainty.  The floating-point precision can be optionally specified with the `FloatType`, `Float64` by default.

```jldoctest
julia> using PhysicalConstants.CODATA2022, Measurements

julia> import PhysicalConstants.CODATA2022: μ_0

julia> μ_0
Vacuum magnetic permeability (μ_0)
Value                         = 1.25663706127e-6 N A^-2
Standard uncertainty          = 2.0e-16 N A^-2
Relative standard uncertainty = 1.6e-10
Reference                     = CODATA 2022

julia> measurement(μ_0)
1.25663706127e-6 ± 2.0e-16 N A^-2

julia> measurement(Float32, μ_0)
1.256637e-6 ± 2.0e-16 N A^-2
```
