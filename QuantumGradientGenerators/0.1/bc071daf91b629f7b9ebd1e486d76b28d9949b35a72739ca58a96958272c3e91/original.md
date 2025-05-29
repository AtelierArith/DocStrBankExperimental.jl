Reset the given gradient vector for a new gradient evaluation.

```julia
resetgradvec!(Ψ̃::GradVector)
```

zeroes out `Ψ̃.grad_states` but leaves `Ψ̃.state` unaffected. This is possible whether or not Ψ̃ supports in-place operations ([`QuantumPropagators.Interfaces.supports_inplace`](@ref))

```julia
resetgradvec!(Ψ̃::GradVector, Ψ)
```

additionally sets `Ψ̃.state` to `Ψ`, which requires that `Ψ̃.state` supports in-place operations.

Returns `Ψ̃`.
