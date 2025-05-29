```
Material(E1, E2, E3, G12, G13, G23, nu12, nu13, nu23, rho,
    S1t=1.0, S1c=1.0, S2t=1.0, S2c=1.0, S3t=1.0, S3c=1.0, S12=1.0, S13=1.0, S23=1.0)
```

Orthotropic material properties. Axis 1 is the main ply axis, axis 2 is the transverse ply axis, and axis 3 is normal to the ply.  For a fiber orientation of zero, axis 1 is along the beam axis.

# Arguments

  * `Ei::float`: Young's modulus along ith axis.
  * `Gij::float`: Shear moduli
  * `nuij::float`: Poisson's ratio.  $nu_ij E_j = nu_ji E_i$
  * `rho::float`: Density
  * `Sit::float`: Tensile strength in ith direction
  * `Sic::float`: Compressive strength in ith direction
  * `Sij::float`: Strength in ij direction
