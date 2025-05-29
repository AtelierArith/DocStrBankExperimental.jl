```julia
initialize!(
    diffusion::SpeedyWeather.HyperDiffusion,
    model::SpeedyWeather.AbstractModel
)

```

Precomputes the hyper diffusion terms in `diffusion` based on the model time step, and possibly with a changing strength/power in the vertical.
