```
random_uniform_translation!(sys::System; shift_size=oneunit(eltype(eltype(sys.coords))),
                            rng=Random.default_rng())
```

Performs a random translation of the coordinates of a randomly selected atom in a [`System`](@ref).

The translation is generated using a uniformly selected direction and uniformly selected length in range [0, 1) scaled by `shift_size` which should have appropriate length units.
