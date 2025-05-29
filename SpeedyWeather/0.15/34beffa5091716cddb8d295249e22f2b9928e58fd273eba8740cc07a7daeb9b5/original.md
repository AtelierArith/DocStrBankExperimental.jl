```julia
transform!(
    diagn::SpeedyWeather.DiagnosticVariables,
    progn::SpeedyWeather.PrognosticVariables,
    lf::Integer,
    random_process::SpeedyWeather.AbstractRandomProcess,
    spectral_transform::SpeedyWeather.SpeedyTransforms.SpectralTransform
)

```

General transform for `random processes <: AbstractRandomProcess`. Takes the spectral `random_pattern` in the prognostic variables and transforms it to spectral space in `diagn.grid.random_pattern`.
