```
transverse_field_ising([elt::Type{<:Number}], [symmetry::Type{<:Sector}],
                       [lattice::AbstractLattice]; J=1.0, g=1.0)
```

MPO for the hamiltonian of the one-dimensional [Transverse-field Ising model](https://en.wikipedia.org/wiki/Transverse-field_Ising_model), as defined by

$$
H = -J\left(\sum_{\langle i,j \rangle} \sigma^z_i \sigma^z_j + g \sum_{i} \sigma^x_i \right)
$$

where the $\sigma^i$ are the spin-1/2 Pauli operators. Possible values for the `symmetry` are `Trivial`, `Z2Irrep` or `FermionParity`.

By default, the model is defined on an infinite chain with unit lattice spacing, with `Trivial` symmetry and with `ComplexF64` entries of the tensors.
