```
Species(element::Gas, Z::Int) -> Species
```

Construct a `Species` from a `Gas` and a charge state. You can also use the `(::Gas)(Z)` convenience constructor like so.

```julia
julia> Xenon(0) == Species(Xenon, 0)
true
```
