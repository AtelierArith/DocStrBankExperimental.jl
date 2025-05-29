```
dynamic(time::Symbol, exc, s::TreatmentSharpness=sharp())
```

Construct a [`DynamicTreatment`](@ref) with fields set by the arguments. By default, `s` is set as [`SharpDesign`](@ref). When working with `@formula`, a wrapper method of `dynamic` calls this method.

# Examples

```jldoctest; setup = :(using DiffinDiffsBase)
julia> dynamic(:month, -1)
Sharp dynamic treatment:
  column name of time variable: month
  excluded relative time: -1

julia> typeof(dynamic(:month, -1))
DynamicTreatment{SharpDesign}

julia> dynamic(:month, -3:-1)
Sharp dynamic treatment:
  column name of time variable: month
  excluded relative time: -3, -2, -1

julia> dynamic(:month, [-2,-1], sharp())
Sharp dynamic treatment:
  column name of time variable: month
  excluded relative time: -2, -1
```
