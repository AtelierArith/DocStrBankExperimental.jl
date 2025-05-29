```
bose_hubbard_model([elt::Type{<:Number}], [symmetry::Type{<:Sector}],
                   [lattice::AbstractLattice];
                   cutoff, t, U, mu, n)
```

MPO for the hamiltonian of the Bose-Hubbard model, as defined by

$$
H = -t \sum_{\langle i,j \rangle} \left( a_{i}^+ a_{j}^- + a_{i}^- a_{j}^+ \right) - \mu \sum_i N_i + \frac{U}{2} \sum_i N_i(N_i - 1).
$$

where $N$ is the bosonic number operator [`a_number`](@ref).

By default, the model is defined on an infinite chain with unit lattice spacing, without any symmetries and with `ComplexF64` entries of the tensors. The Hilbert space is truncated such that at maximum of `cutoff` bosons can be at a single site. If the `symmetry` is not `Trivial`, a fixed (halfinteger) particle number density `n` can be imposed.
