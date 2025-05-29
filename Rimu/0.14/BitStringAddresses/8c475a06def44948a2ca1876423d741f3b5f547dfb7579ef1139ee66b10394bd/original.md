```
near_uniform(BoseFS{N,M}) -> BoseFS{N,M}
```

Create bosonic Fock state with near uniform occupation number of `M` modes with a total of `N` particles.

# Examples

```jldoctest
julia> near_uniform(BoseFS{7,5})
BoseFS{7,5}(2, 2, 1, 1, 1)

julia> near_uniform(FermiFS{3,5})
FermiFS{3,5}(1, 1, 1, 0, 0)
```
