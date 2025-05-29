```
Section(LE_point::PosVector, TE_point::PosVector, aero_model)
```

Create a new wing section with the specified leading edge point, trailing edge point,  and aerodynamic model.

# Arguments

  * `LE_point::PosVector`: Leading edge point coordinates
  * `TE_point::PosVector`: Trailing edge point coordinates
  * `aero_model::AeroModel`: Aerodynamic model type (e.g., INVISCID, POLAR_VECTORS)

# Returns

  * `Section`: A new section with the specified parameters and no aerodynamic data
