```julia
fidelity(ρ, σ)

```

Calculate the fidelity between two density matrices `ρ` and `σ`: $Tr[\sqrt{\sqrt{ρ}σ\sqrt{ρ}}]²$.

# Examples

```julia-repl
julia> ρ = PauliVec[1][1]*PauliVec[1][1]'
julia> σ = PauliVec[3][1]*PauliVec[3][1]'
julia> fidelity(ρ, σ)
0.49999999999999944
```
