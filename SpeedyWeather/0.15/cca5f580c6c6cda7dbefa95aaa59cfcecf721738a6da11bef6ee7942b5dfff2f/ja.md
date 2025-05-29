```julia
add!(
    progn::SpeedyWeather.PrognosticVariables{NF, ArrayType, nsteps, SpectralVariable2D, SpectralVariable3D},
    tracers::SpeedyWeather.Tracer...
)

```

`progn`の予測変数`progn.tracers::Dict`に`tracers`を追加します。
