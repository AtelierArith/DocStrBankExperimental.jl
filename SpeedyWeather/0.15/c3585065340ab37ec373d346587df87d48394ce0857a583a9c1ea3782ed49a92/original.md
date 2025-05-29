```julia
initialize!(
    particles::Array{SpeedyWeather.Particle{NF}, 1},
    progn::SpeedyWeather.PrognosticVariables,
    diagn::SpeedyWeather.DiagnosticVariables,
    particle_advection::SpeedyWeather.ParticleAdvection2D
) -> Any

```

Initialize particle advection time integration: Store u,v interpolated initial conditions in `diagn.particles.u` and `.v`  to be used when particle advection actually executed for first time.
