```julia
SphericalHe(T=Float64;
    age::Number = T(NaN),
    age_sigma::Number = T(NaN),
    offset::Number = zero(T),
    stoppingpower::Number = T(1.189),
    r::Number, 
    dr::Number = one(T), 
    U238::Number, 
    Th232::Number, 
    Sm147::Number = zero(T), 
    U238_matrix::Number = zero(T), 
    Th232_matrix::Number = zero(T), 
    Sm147_matrix::Number = zero(T), 
    agesteps::AbstractRange,
)
```

Construct a `SphericalHe` chronometer representing a mineral with a raw  helium age of `age` ± `age_sigma` [Ma], uniform diffusivity, a radius of `r` [μm], and uniform U, Th and Sm concentrations specified by `U238`, `Th232`, and `Sm147` [PPM]. (A present day U-235/U-238  ratio of 1/137.818 is assumed)

Spatial discretization follows a radius step of `dr` [μm], and temporal discretization follows the age steps specified by the `agesteps` range, in Ma.
