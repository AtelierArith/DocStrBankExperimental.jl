```
LinearSymplecticAttention
```

Implements the linear symplectic attention layers. Analogous to [`GradientLayer`](@ref) it performs mappings that only change the $Q$ or the $P$ part.

This layer preserves symplecticity in the *product-space sense*.

For more information see [`LinearSymplecticAttentionQ`](@ref) and [`LinearSymplecticAttentionP`](@ref).

# Implementation

The coefficients of a [`LinearSymplecticAttention`](@ref) layer is a [`SymmetricMatrix`](@ref):

```jldoctest
using GeometricMachineLearning
using GeometricMachineLearning: params

l = LinearSymplecticAttentionQ(3, 5)
ps = params(NeuralNetwork(Chain(l))).L1

typeof(ps.A) <: SymmetricMatrix

# output

true
```
