```julia
initialize!(
    particles::Array{SpeedyWeather.Particle{NF}, 1},
    progn::SpeedyWeather.PrognosticVariables,
    diagn::SpeedyWeather.DiagnosticVariables,
    particle_advection::SpeedyWeather.ParticleAdvection2D
) -> Any

```

粒子の移流時間積分を初期化します：粒子移流が初めて実行されるときに使用される初期条件を補間したu,vを`diagn.particles.u`および`.v`に格納します。
