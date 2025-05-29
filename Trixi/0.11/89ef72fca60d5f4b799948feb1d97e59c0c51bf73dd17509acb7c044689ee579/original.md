```
IdealGlmMhdMultiIonEquations3D(; gammas, charge_to_mass, 
                               electron_pressure = electron_pressure_zero,
                               initial_c_h = NaN)
```

The ideal compressible multi-ion MHD equations in three space dimensions augmented with a  generalized Langange multipliers (GLM) divergence-cleaning technique. This is a multi-species variant of the ideal GLM-MHD equations for calorically perfect plasmas with independent momentum and energy equations for each ion species. This implementation  assumes that the equations are non-dimensionalized, such that the vacuum permeability is $\mu_0 = 1$.

In case of more than one ion species, the specific heat capacity ratios `gammas` and the charge-to-mass  ratios `charge_to_mass` should be passed as tuples, e.g., `gammas=(1.4, 1.667)`.

The argument `electron_pressure` can be used to pass a function that computes the electron pressure as a function of the state `u` with the signature `electron_pressure(u, equations)`. By default, the electron pressure is zero.

The argument `initial_c_h` can be used to set the GLM divergence-cleaning speed. Note that  `initial_c_h = 0` deactivates the divergence cleaning. The callback [`GlmSpeedCallback`](@ref) can be used to adjust the GLM divergence-cleaning speed according to the time-step size.

References:

  * G. Toth, A. Glocer, Y. Ma, D. Najib, Multi-Ion Magnetohydrodynamics 429 (2010). Numerical  Modeling of Space Plasma Flows, 213–218.
  * A. Rueda-Ramírez, A. Sikstel, G. Gassner, An Entropy-Stable Discontinuous Galerkin Discretization of the Ideal Multi-Ion Magnetohydrodynamics System (2024). Journal of Computational Physics. [DOI: 10.1016/j.jcp.2024.113655](https://doi.org/10.1016/j.jcp.2024.113655).

!!! info "The multi-ion GLM-MHD equations require source terms"
    In case of more than one ion species, the multi-ion GLM-MHD equations should ALWAYS be used with [`source_terms_lorentz`](@ref).

