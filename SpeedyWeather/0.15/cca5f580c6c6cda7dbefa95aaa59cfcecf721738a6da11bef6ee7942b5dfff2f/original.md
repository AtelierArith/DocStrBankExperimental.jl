```julia
add!(
    progn::SpeedyWeather.PrognosticVariables{NF, ArrayType, nsteps, SpectralVariable2D, SpectralVariable3D},
    tracers::SpeedyWeather.Tracer...
)

```

Add `tracers` to the prognostic variables `progn` in `progn.tracers::Dict`.
