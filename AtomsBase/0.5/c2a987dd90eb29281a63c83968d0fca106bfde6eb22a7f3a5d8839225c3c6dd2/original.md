```
atomic_system(atoms::AbstractVector, cell_vectors, periodicity; kwargs...)
```

Construct a [`FlexibleSystem`](@ref) using the passed `atoms` and boundary box and conditions. Extra `kwargs` are stored as custom system properties.

# Examples

Construct a hydrogen molecule in a box, which is periodic only in the first two dimensions

```julia-repl
julia> cell_vectors = [[10.0, 0.0, 0.0], [0.0, 10.0, 0.0], [0.0, 0.0, 10.0]]u"Å"
julia> pbcs = (true, true, false)
julia> hydrogen = atomic_system([:H => [0, 0, 1.]u"bohr",
                                 :H => [0, 0, 3.]u"bohr"],
                                  cell_vectors, pbcs)
```
