```
kitaev_model([elt::Type{<:Number}], [lattice::AbstractLattice];
             t=1.0, mu=1.0, Delta=1.0)
```

MPO for the hamiltonian of the Kitaev model, as defined by

$$
H = \sum_{\langle i,j \rangle} \left(-\frac{t}{2}(c_i^+ c_j^- + c_j^+c_i^-) + \frac{Δ}{2}(c_i^+c_j^+ + c_j^-c_i^-) \right) - \mu \sum_{i} c_i^+ c_i^-
$$

By default, the model is defined on an infinite chain with unit lattice spacing and with `ComplexF64` entries of the tensors.
