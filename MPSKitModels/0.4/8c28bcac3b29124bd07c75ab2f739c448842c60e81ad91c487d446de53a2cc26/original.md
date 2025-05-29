```
heisenberg_XXZ([elt::Type{<:Number}], [symmetry::Type{<:Sector}],
               [lattice::AbstractLattice]; J=1.0, Delta=1.0, spin=1)
```

MPO for the hamiltonian of the XXZ Heisenberg model, as defined by

$$
H = J \left( \sum_{\langle i,j \rangle} S_i^x S_j^x + S_i^y S_j^y + \Delta S_i^z S_j^z \right)
$$

By default, the model is defined on an infinite chain with unit lattice spacing, without any symmetries and with `ComplexF64` entries of the tensors.
