Identify which region of the Weyl chamber a given gate is located in.

```julia
region = weyl_chamber_region(U)
region = weyl_chamber_region(c₁, c₂, c₃)
```

identifies which region of the Weyl chamber the given two-qubit gate `U`, respectively the gate identified by the Weyl chamber coordinates `c₁`, `c₂`, `c₃` (see [`weyl_chamber_coordinates`](@ref)) is in, as a string. Possible outputs are:

  * `"PE"`: gate is in the polyhedron of perfect entanglers.
  * `"W0"`: gate is between the identity and the perfect entanglers.
  * `"W0*"`: gate is between CPHASE(2π) and the perfect entanglers.
  * `"W1"`: gate is between SWAP and the perfect entanglers.

For invalid Weyl chamber coordinates, an empty string is returned.
