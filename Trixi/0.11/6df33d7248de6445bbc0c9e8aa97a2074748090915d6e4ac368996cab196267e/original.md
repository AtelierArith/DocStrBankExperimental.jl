```
IdealGlmMhdMultiIonEquations2D(; gammas, charge_to_mass, 
                               gas_constants = zero(SVector{length(gammas),
                                                            eltype(gammas)}),
                               molar_masses = zero(SVector{length(gammas),
                                                           eltype(gammas)}),
                               ion_ion_collision_constants = zeros(eltype(gammas),
                                                           length(gammas),
                                                           length(gammas)),
                               ion_electron_collision_constants = zero(SVector{length(gammas),
                                                                               eltype(gammas)}),
                               electron_pressure = electron_pressure_zero,
                               electron_temperature = electron_pressure_zero,
                               initial_c_h = NaN)
```

The ideal compressible multi-ion MHD equations in two space dimensions augmented with a  generalized Langange multipliers (GLM) divergence-cleaning technique. This is a multi-species variant of the ideal GLM-MHD equations for calorically perfect plasmas with independent momentum and energy equations for each ion species. This implementation  assumes that the equations are non-dimensionalized such, that the vacuum permeability is $\mu_0 = 1$.

In case of more than one ion species, the specific heat capacity ratios `gammas` and the charge-to-mass  ratios `charge_to_mass` should be passed as tuples, e.g., `gammas=(1.4, 1.667)`.

The ion-ion and ion-electron collision source terms can be computed using the functions  [`source_terms_collision_ion_ion`](@ref) and [`source_terms_collision_ion_electron`](@ref), respectively.

For ion-ion collision terms, the optional keyword arguments `gas_constants`, `molar_masses`, and `ion_ion_collision_constants`  must be provided.  For ion-electron collision terms, the optional keyword arguments `gas_constants`, `molar_masses`,  `ion_electron_collision_constants`, and `electron_temperature` are required.

  * **`gas_constants`** and **`molar_masses`** are tuples containing the gas constant and molar mass of each  ion species, respectively. The **molar masses** can be provided in any unit system, as they are only used to  compute ratios and are independent of the other arguments.
  * **`ion_ion_collision_constants`** is a symmetric matrix that contains coefficients to compute the collision frequencies between pairs of ion species. For example, `ion_ion_collision_constants[2, 3]` contains the collision  coefficient for collisions between the ion species 2 and the ion species 3. These constants are derived using the kinetic theory of gases (see, e.g., *Schunk & Nagy, 2000*). They are related to the collision coefficients $B_{st}$ listed in Table 4.3 of *Schunk & Nagy (2000)*, but are scaled by the molecular mass of ion species $t$ (i.e.,  `ion_ion_collision_constants[2, 3] =` $B_{st}/m_{t}$) and must be provided in consistent physical units  (Schunk & Nagy use $cm^3 K^{3/2} / s$).  See [`source_terms_collision_ion_ion`](@ref) for more details on how these constants are used to compute the collision frequencies.
  * **`ion_electron_collision_constants`** is a tuple containing coefficients to compute the ion-electron collision frequency  for each ion species. They correspond to the collision coefficients `B_{se}` divided by the elementary charge.  The ion-electron collision frequencies can also be computed using the kinetic theory  of gases (see, e.g., *Schunk & Nagy, 2000*). See [`source_terms_collision_ion_electron`](@ref) for more details on how these constants are used to compute the collision frequencies.
  * **`electron_temperature`** is a function with the signature `electron_temperature(u, equations)` that can be used compute the electron temperature as a function of the state `u`. The electron temperature is relevant for the computation  of the ion-electron collision source terms.

The argument `electron_pressure` can be used to pass a function that computes the electron pressure as a function of the state `u` with the signature `electron_pressure(u, equations)`. The gradient of the electron pressure is relevant for the computation of the Lorentz flux and non-conservative term. By default, the electron pressure is zero.

The argument `initial_c_h` can be used to set the GLM divergence-cleaning speed. Note that  `initial_c_h = 0` deactivates the divergence cleaning. The callback [`GlmSpeedCallback`](@ref) can be used to adjust the GLM divergence-cleaning speed according to the time-step size.

References:

  * G. Toth, A. Glocer, Y. Ma, D. Najib, Multi-Ion Magnetohydrodynamics 429 (2010). Numerical  Modeling of Space Plasma Flows, 213–218. [Bib Code: Code: 2010ASPC..429..213T](https://adsabs.harvard.edu/full/2010ASPC..429..213T).
  * A. Rueda-Ramírez, A. Sikstel, G. Gassner, An Entropy-Stable Discontinuous Galerkin Discretization of the Ideal Multi-Ion Magnetohydrodynamics System (2024). Journal of Computational Physics. [DOI: 10.1016/j.jcp.2024.113655](https://doi.org/10.1016/j.jcp.2024.113655).
  * Schunk, R. W., & Nagy, A. F. (2000). Ionospheres: Physics, plasma physics, and chemistry.  Cambridge university press. [DOI: 10.1017/CBO9780511635342](https://doi.org/10.1017/CBO9780511635342).

!!! info "The multi-ion GLM-MHD equations require source terms"
    In case of more than one ion species, the multi-ion GLM-MHD equations should ALWAYS be used with [`source_terms_lorentz`](@ref).

