```
normalize!(A::MPS; (lognorm!)=[])
normalize!(A::MPO; (lognorm!)=[])
```

Change the MPS or MPO `A` in-place such that `norm(A) ≈ 1`. This modifies the data of the tensors within the orthogonality center.

In practice, this evenly spreads `lognorm(A)` over the tensors within the range of the orthogonality center to avoid numerical overflow in the case of diverging norms.

If the norm of the input MPS or MPO is 0, normalizing is ill-defined. In this case, we just return the original MPS or MPO. You can check for this case as follows:

```julia
s = siteinds("S=1/2", 4)
ψ = 0 * random_mps(s)
lognorm_ψ = []
normalize!(ψ; (lognorm!)=lognorm_ψ)
lognorm_ψ[1] == -Inf # There was an infinite norm
```

See also [`normalize`](@ref), [`norm`](@ref), [`lognorm`](@ref).
