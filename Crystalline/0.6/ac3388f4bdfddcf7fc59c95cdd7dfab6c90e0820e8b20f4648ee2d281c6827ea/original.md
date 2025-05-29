```
modulate(flat::UnityFourierLattice{D},
modulation::AbstractVector{ComplexF64}=rand(ComplexF64, length(getcoefs(flat))),
expon::Union{Nothing, Real}=nothing, Gs::Union{ReciprocalBasis{D}, Nothing}=nothing)
                        --> ModulatedFourierLattice{D}
```

Derive a concrete, modulated Fourier lattice from a `UnityFourierLattice` `flat` (containing the *interrelations* between orbit coefficients), by  multiplying the "normalized" orbit coefficients by a `modulation`, a *complex* modulating vector (in general, should be complex; otherwise restores unintended symmetry to the lattice). Distinct `modulation` vectors produce distinct  realizations of the same lattice described by the original `flat`. By default, a random complex vector is used.

An exponent `expon` can be provided, which introduces a penalty term to short- wavelength features (i.e. high-|G| orbits) by dividing the orbit coefficients by |G|^`expon`; producing a "simpler" and "smoother" lattice boundary when `expon > 0` (reverse for `expon < 0`). This basically amounts to a  continuous "simplifying" operation on the lattice (it is not necessarily a  smoothing operation; it simply suppresses "high-frequency" components). If `expon = nothing`, no rescaling is performed. If `Gs` is provided as `nothing`, the orbit norm is computed in the reciprocal lattice basis (and, so, may not strictly speaking be a norm if the lattice basis is not cartesian); to account for the basis explicitly, `Gs` must be provided as a [`ReciprocalBasis`](@ref), see also [`normscale`](@ref).
