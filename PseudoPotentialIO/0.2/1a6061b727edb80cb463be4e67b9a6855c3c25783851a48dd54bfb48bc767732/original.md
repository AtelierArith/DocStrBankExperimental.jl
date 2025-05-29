```julia
abstract type AbstractPsP
```

Abstract type representing a pseudopotential.

The structure of the data should facilitate efficient computations.

Required methods:

```julia
# A unique string, usually a hash or checksum.
function identifier(file::AbstractPsP)::AbstractString end
# The symbol of the element for which the pseudopotential is constructed (e.g. `"Ag"`)
function elemental_symbol(psp::AbstractPsP)::AbstractString end
# The maximum angular momentum channel
function max_angular_momentum(psp::AbstractPsP)::Integer end
# The number of non-local projector radial parts for angular momentum `l`
function n_projector_radials(psp::AbstractPsP, l::Integer)::Integer end
# The number of chi function radial parts for angular momentum `l`
function n_chi_function_radials(psp::AbstractPsP, l::Integer)::Integer end
# The pseudo-atomic valence charge
function valence_charge(psp::AbstractPsP)::Real end
# The charge of the atom which was pseudized (e.g. 8 for Oxygen)
function atomic_charge(psp::AbstractPsP)::Real end
# Whether the pseudopotential is a norm-conserving pseudopotential
function is_norm_conserving(psp::AbstractPsP)::Bool end
# Whether the pseudopotential is an ultrasoft pseudopotential
function is_ultrasoft(psp::AbstractPsP)::Bool end
# Whether the pseudopotential is a projector-augmented wave pseudopotential
function is_paw(psp::AbstractPsP)::Bool end
# Whether the pseudopotential supports spin-orbit coupled calculations
function has_spin_orbit(psp::AbstractPsP)::Bool end
# Whether the pseudopotential contains a core charge density (i.e. supports non-linear core
# correction)
function has_core_density(psp::AbstractPsP)::Bool end
# Whether the pseudopotential contains a valence charge density (i.e. has support for
# constructing a tailored guess charge density)
function has_valence_density(psp::AbstractPsP)::Bool end
# Whether pseudopotential contains chi functions for the valence electrons (i.e.
# has support for computing tailored orbital-projected quantitites)
function has_chi_functions(psp:AbstractPsP)::Bool end
# The projector coupling coefficients for angular momentum `l`
function projector_coupling(psp::AbstractPsP, l::Integer)::Matrix{Real} end
# Radial distance where the local potential decays to zero within a tolerance `tol`
function local_potential_cutoff_radius(psp::AbstractPsP; tol) end
# Radial distance where the `n`th non-local projector at angular momentum `l` decays to
# zero within a tolerance `tol`
function projector_cutoff_radius(psp::AbstractPsP, l, n; tol) end
# Radial distance where the `n`th chi function at angular momentum `l` decays to
# zero within a tolerance `tol`
function chi_function_cutoff_radius(psp::AbstractPsP, l, n; tol) end
# Radial distance where the valence charge density decays to zero within a tolerance `tol`
function valence_charge_density_cutoff_radius(psp::AbstractPsP; tol) end
# Radial distance where the core charge density decays to zero within a tolerance `tol`
function core_charge_density_cutoff_radius(psp::AbstractPsP; tol) end
# Returns a function which evaulates the local potential at a real-space radial coordinate
function local_potential_real(psp::AbstractPsP) end
# Returns a function which evaulates the `n`th non-local projector with angular momentum
# `l` at a real-space radial coordinate
function projector_real(psp::AbstractPsP, l, n) end
# Returns a function which evaulates the `n`th chi function with angular momentum
# `l` at a real-space radial coordinate
function chi_function_real(psp::AbstractPsP, l, n) end
# Returns a function which evaulates the valence charge density at a real-space
# radial coordinate
function valence_charge_density_real(psp::AbstractPsP) end
# Returns a function which evaulates the core charge density at a real-space
# radial coordinate
function core_charge_density_real(psp::AbstractPsP) end
# Returns a function which evaulates the local potential at a fourier-space radial
# coordinate
function local_potential_fourier(psp::AbstractPsP) end
# Returns a function which evaulates the `n`th non-local projector with angular momentum
# `l` at a fourier-space radial coordinate
function projector_fourier(psp::AbstractPsP, l, n) end
# Returns a function which evaulates the `n`th chi function with angular momentum
# `l` at a fourier-space radial coordinate
function chi_function_fourier(psp::AbstractPsP, l, n) end
# Returns a function which evaulates the valence charge density at a fourier-space
# radial coordinate
function valence_charge_density_fourier(psp::AbstractPsP) end
# Returns a function which evaulates the core charge density at a fourier-space
# radial coordinate
function core_charge_density_fourier(psp::AbstractPsP) end
# The pseudo-potential energy correction
function pseudo_energy_correction(psp::AbstractPsP) end
```
