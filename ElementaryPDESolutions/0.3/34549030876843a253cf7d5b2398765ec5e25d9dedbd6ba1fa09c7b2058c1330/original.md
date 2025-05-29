```
solve_elastostatic(Q::NTuple{N,Polynomial{N,T}};μ=1,ν=1)
```

Compute a vector of polynomials `U` satisfying `μ/(1-2ν) ∇(div U) + μΔU = Q`. `Q` is required to be homogeneous.

# Examples

```jldoctest
julia> Q = (Polynomial((1,2)=>1), Polynomial((0,0)=>1))
(xy², 1)

julia> P = solve_elastostatic(Q;ν=1//2)
(-1//8xy + 1//480x⁵ + 1//32x³y² + 1//24xy⁴, 3//16x² + 1//16y² - 1//120y⁵ - 1//96x⁴y - 1//32x²y³)
```
