```
struct BraidingTensor{T,S<:IndexSpace} <: AbstractTensorMap{T, S, 2, 2}
BraidingTensor(V1::S, V2::S, adjoint::Bool=false) where {S<:IndexSpace}
```

Specific subtype of [`AbstractTensorMap`](@ref) for representing the braiding tensor that braids the first input over the second input; its inverse can be obtained as the adjoint.

It holds that `domain(BraidingTensor(V1, V2)) == V1 ⊗ V2` and `codomain(BraidingTensor(V1, V2)) == V2 ⊗ V1`.
