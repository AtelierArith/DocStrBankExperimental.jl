```
acousticcouplingpanels(self::FEMMAcoustSurf, geom::NodalField, u::NodalField{T}) where {T}
```

Compute the acoustic pressure-structure coupling matrix.

The acoustic pressure-nodal force matrix transforms the pressure distributed along the surface to forces acting on the nodes of the finite element model. Its transpose transforms displacements (or velocities, or accelerations) into the normal component of the displacement (or velocity, or acceleration) along the surface.

# Arguments

  * `geom`=geometry field
  * `u` = displacement field

!!! note



  * `n` = outer normal (pointing into the acoustic medium).
  * The pressures along the surface are assumed constant (uniform) along   each finite element –- panel. The panel pressures are assumed to be   given the same numbers as the serial numbers of the finite elements in   the set.
