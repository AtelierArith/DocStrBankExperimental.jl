```
normalize(A::QuantumObject, p::Real)
unit(A::QuantumObject, p::Real)
```

Return normalized [`QuantumObject`](@ref) so that its `p`-norm equals to unity, i.e. `norm(A, p) == 1`.

Support for the following types of [`QuantumObject`](@ref):

  * If `A` is [`Ket`](@ref) or [`Bra`](@ref), default `p = 2`
  * If `A` is [`Operator`](@ref), default `p = 1`

!!! note
    `unit` is a synonym of `normalize`.


Also, see [`norm`](@ref) about its definition for different types of [`QuantumObject`](@ref).
