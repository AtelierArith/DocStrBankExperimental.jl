```
setpanel(data, idname, timename; step, reftype, rotation)
setpanel(id::AbstractArray, time::AbstractArray; step, reftype, rotation)
```

Declare a [`PanelStructure`](@ref) which is required for certain operations such as [`lag`](@ref) and [`diff`](@ref). Unit IDs and time values can be provided either as a table containing the relevant columns or as arrays. `timestep` must be specified unless the `time` array is a [`ScaledArray`](@ref) that is returned by [`settime`](@ref).

# Arguments

  * `data`: a `Tables.jl`-compatible data table.
  * `idname::Union{Symbol,Integer}`: the name of the column in `data` that contains unit IDs.
  * `timename::Union{Symbol,Integer}`: the name of the column in `data` that contains time values.
  * `id::AbstractArray`: the array containing unit IDs (only needed for the alternative method).
  * `time::AbstractArray`: the array containing time values (only needed for the alternative method).

# Keywords

  * `step=nothing`: the length of each time interval; try `step=one(eltype(time))` if not specified.
  * `reftype::Type{<:Signed}=Int32`: the element type of the reference values for [`PanelStructure`](@ref).
  * `rotation=nothing`: rotation groups in a rotating sampling design; use [`RotatingTimeValue`](@ref)s as reference values.

!!! note
    If the underlying data used to create the [`PanelStructure`](@ref) are modified. The changes will not be reflected in the existing instances of [`PanelStructure`](@ref). A new instance needs to be created with `setpanel`.

