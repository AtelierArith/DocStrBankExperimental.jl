```
pressure_drop(f::Fluid, b::Bend)
```

Computes the pressure drop of a `fluid` flowing through a `bend`.

So far, we only support 90-degree bends, see Spedding, P.L., Bernard, E. and McNally, G.M., ‘Fluid ﬂow through 90 degree bends’, Dev. Chem. Eng Mineral Process, 12: 107–128, 2004.

# Arguments

  * `f::Fluid`: the fluid flowing through the tube
  * `b::Bend`: the valve through which the fluid flows

# Returns

  * `DynamicQuantity.AbstractQuantity`: the pressure drop of the fluid flowing through the tube
