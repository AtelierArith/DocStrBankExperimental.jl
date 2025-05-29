```julia
MultipleDomain(T=Float64, C=PlanarAr;
    age::AbstractVector,
    age_sigma::AbstractVector,
    fraction_experimental::AbstractVector,
    fraction_experimental_sigma::Number=T(0.01),
    tsteps_experimental::AbstractVector,
    Tsteps_experimental::AbstractVector,
    fit::AbstractVector,
    offset::Number = zero(T),
    fuse::Bool = true,
    volume_fraction::AbstractVector,
    r::Number = 100,
    dr::Number = one(T),
    K40::Number = 16.34, 
    agesteps::AbstractRange,
    tsteps::AbstractRange=reverse(agesteps),
)
```

Construct a `MultipleDomain` diffusion chronometer given an observed argon release spectrum, degassing schedule, where domain is represented by a  `PlanarAr` or `SphericalAr` chronometer.

Domain diffusivity and volume parameters must be supplied as vectors `Ea` [kJ/mol], `lnD0a2` [log(1/s)], and `volume_fraction` [unitless] obtained by separately fitting the release spectrum (the former two as an `MDDiffusivity` object).

See also: `MDDiffusivity`, `PlanarAr`, `SphericalAr`, `degas!`
