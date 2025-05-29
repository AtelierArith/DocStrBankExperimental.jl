```julia
partial_trace(ρ, sys_dim, dim_2_keep)

```

Calculate the partial trace of the density matrix `ρ`. Assume `ρ` is in the tensor space of $ℋ₁⊗ℋ₂⊗…$, `sys_dim` is an array of the corresponding sub-system dimensions. `dim_2_keep` is an array of the indices whose corresponding subsystems are not traced out.

# Examples

```julia-repl
julia> ρ1 = [0.4 0.2; 0.2 0.6]; ρ2 = [0.5 0; 0 0.5];
julia> partial_trace(ρ1⊗ρ2, [2, 2], [1])
2×2 Array{Float64,2}:
 0.4  0.2
 0.2  0.6
```
