```Julia
gaussgravitation(U::UnitSystem) = sqrt(gravitation(U)*solarmass(U)/astronomicalunit(U)^3)
```

Gaussian  gravitational constant `k` of Newton's laws (Hz or rad⋅D⁻¹).

```Julia
julia> gaussgravitation(Engineering)
1.9909836764714663e-7

julia> gaussgravitation(MetricGradian)
1.2674995749028351e-5

julia> gaussgravitation(MetricDegree)
1.1407496174125516e-5

julia> gaussgravitation(MetricArcminute)
0.000684449770447531

julia> gaussgravitation(MetricArcsecond)
0.041066986226851857

juila> gaussgravitation(MPH)
0.000716754123529728

julia> gaussgravitation(IAU)
0.017202098964713468
```
