```
speed(θ,P::Planet) = cos(θ)*radius(θ,P)*angularfrequency(P)
```

Velocity component due to sidereal rotation of `Planet` at latitude `θ` (m⋅s⁻¹).

```Julia
julia> speed(0,Earth)
465.1010942547186
```
