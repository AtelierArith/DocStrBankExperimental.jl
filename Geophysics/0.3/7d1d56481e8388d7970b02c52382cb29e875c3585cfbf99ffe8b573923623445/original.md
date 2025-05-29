```
gravity(ϕ,P::Planet)
```

Calculate total `gravity` at geodetic latitude `ϕ` on `Planet` surface (m⋅s⁻²).

```Julia
julia> gravity(0,Earth)
9.780325333855085

julia> gravity(π/2,Earth)
9.832184939227085
```
