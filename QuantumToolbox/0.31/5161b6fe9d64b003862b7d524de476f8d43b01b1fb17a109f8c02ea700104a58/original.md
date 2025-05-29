```
(A::QuantumObjectEvolution)(ψ, p, t)
```

Apply the time-dependent [`QuantumObjectEvolution`](@ref) object `A` to the input state `ψ` at time `t` with parameters `p`. Out-of-place version of [`(A::QuantumObjectEvolution)(ψout, ψin, p, t)`](@ref). The output state is stored in a new [`QuantumObject`](@ref) object. This function mimics the behavior of a `AbstractSciMLOperator` object.
