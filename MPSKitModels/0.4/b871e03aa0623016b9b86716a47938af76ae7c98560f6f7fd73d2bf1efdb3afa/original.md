```
heisenberg_XYZ([elt::Type{<:Number}], [lattice::AbstractLattice];
    Jx=1.0, Jy=1.0, Jz=1.0, spin=1)
```

MPO for the hamiltonian of the XYZ Heisenberg model, defined by

$$
H = \sum_{\langle i,j \rangle} \left( J^x S_i^x S_j^x + J^y S_i^y S_j^y + J^z S_i^z S_j^z \right)
$$

By default, the model is defined on an infinite chain with unit lattice spacing and with `ComplexF64` entries of the tensors.
