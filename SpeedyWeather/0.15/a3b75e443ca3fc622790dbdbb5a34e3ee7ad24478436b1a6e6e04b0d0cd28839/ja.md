```julia
struct JablonowskiWilliamsonParams
    η₀::Float64  # conversion from σ to Jablonowski's ηᵥ-coordinates
    u₀::Float64  # max amplitude of zonal wind [m/s]
    perturb_lat::Float64  # perturbation centred at [˚N]
    perturb_lon::Float64  # perturbation centred at [˚E]
    perturb_uₚ::Float64  # perturbation strength [m/s]
    perturb_radius::Float64  # radius of Gaussian perturbation in units of Earth's radius [1]
end

# Default values as in Jablonowski
const default_params = JablonowskiWilliamsonParams(η₀=0.5, u₀=10.0, perturb_lat=30.0, perturb_lon=0.0, perturb_uₚ=1.0, perturb_radius=0.1)
```
