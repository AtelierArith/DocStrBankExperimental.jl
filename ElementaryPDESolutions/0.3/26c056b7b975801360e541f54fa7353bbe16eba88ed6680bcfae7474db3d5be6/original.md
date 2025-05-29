```
solve_helmholtz(Q::Polynomial;k=1)
```

Return the unique polynomial `P` satisfying `ΔP + k²P = Q`.

# Examples

```jldoctest
julia> Q = Polynomial((1,2)=>1)
xy²

julia> P = solve_helmholtz(Q, k=1)
-2.0x + xy²
```
