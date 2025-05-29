```julia
ApatiteHe(T=Float64;
    age::Number = T(NaN),
    age_sigma::Number = T(NaN),
    offset::Number = zero(T),
    r::Number, 
    dr::Number = one(T), 
    U238::Number, 
    Th232::Number, 
    Sm147::Number = zero(T), 
    U238_matrix::Number = zero(T), 
    Th232_matrix::Number = zero(T), 
    Sm147_matrix::Number = zero(T), 
    volumeweighting::Symbol = :spherical,
    agesteps::AbstractRange,
)
```

Construct an `ApatiteHe` chronometer representing an apatite with a raw  helium age of `age` ± `age_sigma` [Ma], a  radius of `r` [μm], and uniform  U, Th and Sm concentrations specified by `U238`, `Th232`, and `Sm147` [PPMW].  A present day U-235/U-238 ratio of 1/137.818 is assumed.

Spatial discretization follows a radius step of `dr` [μm], and temporal discretization follows the age steps specified by the `agesteps` range, in Ma.
