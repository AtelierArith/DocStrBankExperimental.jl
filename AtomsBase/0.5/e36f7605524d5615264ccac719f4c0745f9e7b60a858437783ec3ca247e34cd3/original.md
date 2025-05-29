```
periodic_system(atoms::AbstractVector, box; fractional=false, kwargs...)
```

Construct a [`FlexibleSystem`](@ref) with all boundaries of the `box` periodic (standard setup for modelling solid-state systems). If `fractional` is true, atom coordinates are given in fractional (and not in Cartesian) coordinates. Extra `kwargs` are stored as custom system properties.

# Examples

Setup a hydrogen molecule inside periodic BCs:

```julia-repl
julia> cell_vectors = ([10.0, 0.0, 0.0]u"Å", [0.0, 10.0, 0.0]u"Å", [0.0, 0.0, 10.0]u"Å")
julia> hydrogen = periodic_system([:H => [0, 0, 1.]u"bohr",
                                   :H => [0, 0, 3.]u"bohr"],
                                  cell_vectors)
```

Setup a silicon unit cell using fractional positions

```julia-repl
julia> box = 10.26 / 2 * [[0, 0, 1], [1, 0, 1], [1, 1, 0]]u"bohr"
julia> silicon = periodic_system([:Si =>  ones(3)/8,
                                  :Si => -ones(3)/8],
                                 box, fractional=true)
```
