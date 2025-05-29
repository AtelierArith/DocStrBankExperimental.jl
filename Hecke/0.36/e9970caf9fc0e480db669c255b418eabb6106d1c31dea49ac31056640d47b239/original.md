```
k3_lattice()
```

Return the integer lattice corresponding to the Beauville-Bogomolov-Fujiki form associated to a K3 surface.

# Examples

```jldoctest
julia> L = k3_lattice();

julia> is_unimodular(L)
true

julia> signature_tuple(L)
(3, 0, 19)
```
