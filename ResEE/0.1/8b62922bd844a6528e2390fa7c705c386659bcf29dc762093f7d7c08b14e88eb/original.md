```
get_rho_M_ijmap(state_istate::Vector{Int}; S::Real, L::Int, LA::Int=0)
```

return the intermediate matrix index (i, j) mapping for constrainted system.

# Example

```juila-repl
julia> rho, M, ij_istate = get_rho_M_ijmap(state_istate, Float64; S=S, L=L)
```
