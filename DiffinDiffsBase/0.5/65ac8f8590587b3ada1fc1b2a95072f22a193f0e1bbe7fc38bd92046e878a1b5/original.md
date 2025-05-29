```
PanelStructure{R<:Signed, IP<:AbstractVector, TP<:AbstractVector}
```

Panel data structure defined by unique combinations of unit ids and time periods. It contains the information required for certain operations such as [`lag`](@ref) and [`diff`](@ref). See also [`setpanel`](@ref).

# Fields

  * `refs::Vector{R}`: reference values that allow obtaining time gaps by taking differences.
  * `invrefs::Dict{R, Int}`: inverse map from `refs` to indices.
  * `idpool::IP`: unique unit ids.
  * `timepool::TP`: sorted unique time periods.
  * `laginds::Dict{Int, Vector{Int}}`: a map from lag distances to vectors of indices of lagged values.
