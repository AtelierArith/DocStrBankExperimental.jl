```julia
renormed(model, f)

```

Renormalizes the model `m` to have total flux `f*flux(m)`. This can also be done directly by calling `Base.:*` i.e.,

```julia-repl
julia> renormed(m, f) == f*M
true
```
