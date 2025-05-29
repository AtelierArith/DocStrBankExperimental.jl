```
orbit(K::Fatou.Define)
orbit(u::Function, ∂, orbit, depth, n)
```

Plot funciton compositions of the primary `Fatou.Define` function up to any `depth` including cobweb plot with an `orbit` depth from the `x0` start point.

# Examples

```Julia
julia> juliafill("z^2-0.67",∂=[-1.25,1.5],x0=1.25,orbit=17,depth=3) |> orbit
```
