```
solve_laplace(Q::Polynomial)
```

Return a polynomial `P` satisfying `ΔP = Q`. `Q` is required to be homogeneous.

# Examples

```jldoctest
julia> Q = Polynomial((1,0)=>1.0)
x

julia> P = solve_laplace(Q)
0.125xy² + 0.125x³
```
