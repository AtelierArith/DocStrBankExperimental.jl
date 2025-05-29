```
tj_model([elt::Type{<:Number}], [particle_symmetry::Type{<:Sector}],
              [spin_symmetry::Type{<:Sector}], [lattice::AbstractLattice];
              t, J, mu, slave_fermion::Bool=false)
```

MPO for the hamiltonian of the t-J model, as defined by

$$
H = -t \sum_{\langle i,j \rangle, \sigma}
    (\tilde{e}^\dagger_{i,\sigma} \tilde{e}_{j,\sigma} + h.c.)
    + J \sum_{\langle i,j \rangle}(\mathbf{S}_i \cdot \mathbf{S}_j - \frac{1}{4} n_i n_j)
    - \mu \sum_i n_i
$$

where $\tilde{e}_{i,\sigma}$ is the electron operator with spin $\sigma$ restrict to the no-double-occupancy subspace. 
