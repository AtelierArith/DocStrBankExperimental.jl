Minimum of adjusted p-value combination

# Examples

```jldoctest
julia> pv = PValues([0.01, 0.02, 0.3, 0.5]);

julia> combine(pv, Minimum(BenjaminiHochberg()))
0.04

julia> combine(pv, Minimum(ForwardStop()))
0.01005033585350145
```
