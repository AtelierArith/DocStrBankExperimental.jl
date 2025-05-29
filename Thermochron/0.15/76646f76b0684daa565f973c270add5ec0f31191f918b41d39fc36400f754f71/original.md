```julia
PlanarAr(T=Float64;
    age::Number = T(NaN),
    age_sigma::Number = T(NaN),
    offset::Number = zero(T),
    r::Number, 
    dr::Number = one(T), 
    K40::Number=16.34, 
    agesteps::AbstractRange,
)
```

Construct an `PlanarAr` chronometer representing a mineral with a raw  argon age of `age` ± `age_sigma` [Ma], a uniform diffusivity, a radius of `r` [μm], and uniform K-40 concentrations specified by `K40` [PPM].

Spatial discretization follows a halfwidth step of `dr` [μm], and temporal discretization follows the age steps specified by the `agesteps` range, in Ma.
