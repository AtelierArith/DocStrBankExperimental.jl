```
set_exchange!(sys::System, J, bond::Bond; biquad=0)
```

Sets an exchange interaction $𝐒_i⋅J 𝐒_j$ along the specified `bond`. This interaction will be propagated to equivalent bonds in consistency with crystal symmetry. Any previous interactions on these bonds will be overwritten. The parameter `bond` has the form `Bond(i, j, offset)`, where `i` and `j` are atom indices within the unit cell, and `offset` is a displacement in unit cells.

As a convenience, scalar `J` can be used to specify a Heisenberg interaction. Also, the function [`dmvec(D)`](@ref dmvec) can be used to construct the antisymmetric part of the exchange, where `D` is the Dzyaloshinskii-Moriya pseudo-vector. The resulting interaction will be $𝐃⋅(𝐒_i×𝐒_j)$.

The optional numeric parameter `biquad` multiplies a scalar biquadratic interaction, $(𝐒_i⋅𝐒_j)^2$, with [Interaction Renormalization](@ref) if appropriate. For more general interactions, use [`set_pair_coupling!`](@ref) instead.

# Examples

```julia
using LinearAlgebra

# Set a Heisenberg and DM interaction: 2Si⋅Sj + D⋅(Si×Sj)
D = [0, 0, 3]
set_exchange!(sys, 2I + dmvec(D), bond)

# The same interaction as an explicit exchange matrix
J = [2 3 0;
    -3 2 0;
     0 0 2]
set_exchange!(sys, J, bond)
```
