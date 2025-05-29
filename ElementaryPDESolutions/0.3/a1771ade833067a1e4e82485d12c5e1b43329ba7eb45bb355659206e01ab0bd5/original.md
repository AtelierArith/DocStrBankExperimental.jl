```
solve_bilaplace(Q::Polynomial)
```

Compute a polynomial solution to `Δ²P = Q`. `Q` is required to be homogeneous.

# Examples

```jldoctest
julia> Q = Polynomial((1,0)=>1)
x

julia> P = solve_bilaplace(Q)
1//192x⁵ + 1//96x³y² + 1//192xy⁴
```
