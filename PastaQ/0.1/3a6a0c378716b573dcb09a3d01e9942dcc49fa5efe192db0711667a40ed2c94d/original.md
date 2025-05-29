```
fidelity_bound(ρ::Union{MPO, LPDO}, σ::Union{MPO, LPDO})
```

Compute the the following lower bound of the fidelity:

`F̃(ρ,σ) = trace[ρ̃† σ̃]`

where `ρ̃` and `σ̃` are the normalized density matrices.

The bound becomes tight when the target state is nearly pure.
