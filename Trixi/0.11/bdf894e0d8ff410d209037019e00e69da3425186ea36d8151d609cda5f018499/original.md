```
flux_nonconservative_powell_local_symmetric(u_ll, orientation::Integer,
                                            equations::IdealGlmMhdEquations2D,
                                            nonconservative_type::NonConservativeLocal,
                                            nonconservative_term::Integer)
```

Local part of the Powell and GLM non-conservative terms. Needed for the calculation of the non-conservative staggered "fluxes" for subcell limiting. See, e.g.,

  * Rueda-Ramírez, Gassner (2023). A Flux-Differencing Formula for Split-Form Summation By Parts Discretizations of Non-Conservative Systems. https://arxiv.org/pdf/2211.14009.pdf.

This function is used to compute the subcell fluxes in dg*2d*subcell_limiters.jl.
