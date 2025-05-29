```
solve_elastodynamics(Q::NTuple{N,Polynomial{N,T}};ρ=1,μ=1,ν=1/4,ω=1)
```

Compute a vector of polynomials `U` satisfying `-μ/(1-2ν) ∇(div U) - μ ΔU - μ k₂² U = Q`.

# Examples

```jldoctest
julia> Q = (Polynomial((2,1)=>1),Polynomial((1,0)=>1))
(x²y, x)

julia> P = solve_elastodynamics(Q;μ=1)
(-6//1y + x²y, -3//1x)
```
