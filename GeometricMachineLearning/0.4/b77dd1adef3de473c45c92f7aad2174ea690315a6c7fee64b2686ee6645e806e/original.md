```
VolumePreservingLowerLayer(dim)
```

Make an instance of `VolumePreservingLowerLayer` for a specific system dimension.

See the documentation for [`VolumePreservingFeedForwardLayer`](@ref).

# Examples

We apply the `VolumePreservingLowerLayer` with matrix:

$$
L = \begin{pmatrix} 0 & 0 \\ 1 & 0 \end{pmatrix}
$$

to a vector:

$$
x = \begin{pmatrix} 1 \\ 1 \end{pmatrix}
$$

```jldoctest
using GeometricMachineLearning

l = VolumePreservingLowerLayer(2, identity; use_bias=false)
A = LowerTriangular([1,], 2)
ps = (weight = A, )
x = ones(eltype(A), 2)

l(x, ps)

# output

2×1 Matrix{Int64}:
 1
 2
```

# Arguments

The constructor can be called with the optional arguments:

  * `activation=tanh`: the activation function.
  * `use_bias::Bool=true` (keyword argument): specifies whether a bias should be used.
