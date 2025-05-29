```
flux_nonconservative_powell_local_symmetric(u_ll, u_rr,
                                            orientation::Integer,
                                            equations::IdealGlmMhdEquations2D)
```

Non-symmetric two-point flux discretizing the nonconservative (source) term of Powell and the Galilean nonconservative term associated with the GLM multiplier of the [`IdealGlmMhdEquations2D`](@ref).

This implementation uses a non-conservative term that can be written as the product of local and symmetric parts. It is equivalent to the non-conservative flux of Bohm et al. [`flux_nonconservative_powell`](@ref) for conforming meshes but it yields different results on non-conforming meshes(!). On curvilinear meshes this formulation applies the local normal direction compared to the averaged one used in [`flux_nonconservative_powell`](@ref).

The two other flux functions with the same name return either the local or symmetric portion of the non-conservative flux based on the type of the nonconservative*type argument, employing multiple dispatch. They are used to compute the subcell fluxes in dg*2d*subcell*limiters.jl.

## References

  * Rueda-Ramírez, Gassner (2023). A Flux-Differencing Formula for Split-Form Summation By Parts Discretizations of Non-Conservative Systems. https://arxiv.org/pdf/2211.14009.pdf.
