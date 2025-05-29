```julia
transform!(
    diagn::SpeedyWeather.DiagnosticVariables,
    progn::SpeedyWeather.PrognosticVariables,
    lf::Integer,
    random_process::SpeedyWeather.NoRandomProcess,
    spectral_transform::SpeedyWeather.SpeedyTransforms.SpectralTransform
)

```

`NoRandomProcess` does not need to transform any random pattern from spectral to grid space.
