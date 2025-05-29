```
flux_nonconservative_powell(u_ll, u_rr, orientation::Integer,
                            equations::IdealGlmMhdEquations3D)
flux_nonconservative_powell(u_ll, u_rr,
                            normal_direction::AbstractVector,
                            equations::IdealGlmMhdEquations3D)
```

Non-symmetric two-point flux discretizing the nonconservative (source) term of Powell and the Galilean nonconservative term associated with the GLM multiplier of the [`IdealGlmMhdEquations3D`](@ref).

On curvilinear meshes, the implementation differs from the reference since we use the averaged  normal direction for the metrics dealiasing.

## References

  * Marvin Bohm, Andrew R.Winters, Gregor J. Gassner, Dominik Derigs, Florian Hindenlang, Joachim Saur An entropy stable nodal discontinuous Galerkin method for the resistive MHD equations. Part I: Theory and numerical verification [DOI: 10.1016/j.jcp.2018.06.027](https://doi.org/10.1016/j.jcp.2018.06.027)
