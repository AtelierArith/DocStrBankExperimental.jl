```julia
initialize!(
    diffusion::SpeedyWeather.HyperDiffusion,
    G::SpeedyWeather.AbstractGeometry,
    L::SpeedyWeather.AbstractTimeStepper
)

```

Precomputes the hyper diffusion terms for all layers based on the model time step in `L`, the vertical level sigma level in `G`.
