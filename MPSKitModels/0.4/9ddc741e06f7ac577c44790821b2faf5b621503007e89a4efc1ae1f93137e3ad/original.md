```
heisenberg_XXX([elt::Type{<:Number}], [symmetry::Type{<:Sector}],
                       [lattice::AbstractLattice]; J=1.0, spin=1)
```

MPO for the hamiltonian of the isotropic Heisenberg model, as defined by

$$
H = J \sum_{\langle i,j \rangle} \vec{S}_i \cdot \vec{S}_j
$$

where $\vec{S} = (S^x, S^y, S^z)$.

By default, the model is defined on an infinite chain with unit lattice spacing, without any symmetries and with `ComplexF64` entries of the tensors.

See also [`heisenberg_XXZ`](@ref) and [`heisenberg_XYZ`](@ref).
