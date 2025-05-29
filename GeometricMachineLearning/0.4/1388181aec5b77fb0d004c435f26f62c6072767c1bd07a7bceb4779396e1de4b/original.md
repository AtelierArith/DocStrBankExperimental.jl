```
SymplecticAttention
```

Implements the symplectic attention layers. See [`LinearSymplecticAttention`](@ref).

# Keys

It stores the following key:

  * `activation::``AbstractSoftmax`

# Constructors

See [`SymplecticAttentionQ`](@ref) and [`SymplecticAttentionP`](@ref).

# Implementation

`SymplecticAttention` is similar to [`MultiHeadAttention`](@ref) or [`VolumePreservingAttention`](@ref) in that it computes the scalar products of all vectors in a sequence of input vectors:

$$
C = Q^TAQ,
$$

where $Q$ is the $q$-part of an input $Z$ (see [`QPT`](@ref)). The matrix $A$ is a weighting that can either be symmetric or skew-symmetric (this can be adjusted with the key-word `symmetric::Bool`).

# Extended help

The symplectic attention mechanism is derived via computing the gradient of a separable Hamiltonian, as is also done in [`GSympNet`](@ref)s.
