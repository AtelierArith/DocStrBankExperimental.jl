```
normalize(A::MPS; (lognorm!)=[])
normalize(A::MPO; (lognorm!)=[])
```

Return a new MPS or MPO `A` that is the same as the original MPS or MPO but with `norm(A) ≈ 1`.

In practice, this evenly spreads `lognorm(A)` over the tensors within the range of the orthogonality center to avoid numerical overflow in the case of diverging norms.

See also [`normalize!`](@ref), [`norm`](@ref), [`lognorm`](@ref).
