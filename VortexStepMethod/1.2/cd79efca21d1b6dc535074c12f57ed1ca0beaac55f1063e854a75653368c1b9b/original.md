```
add_section!(wing::Wing, LE_point::PosVector, TE_point::PosVector, 
             aero_model, aero_data::AeroData=nothing)
```

Add a new section to the wing.

# Arguments:

  * wing::Wing: The [Wing](@ref) to which a section shall be added
  * LE_point::PosVector: [PosVector](@ref) of the point on the side of the leading edge
  * TE_point::PosVector: [PosVector](@ref) of the point on the side of the trailing edge
  * `aero_model`::AeroModel: [AeroModel](@ref)
  * `aero_data`::AeroData: See [AeroData](@ref)
