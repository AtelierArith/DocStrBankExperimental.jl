```
hubbard_model([elt::Type{<:Number}], [particle_symmetry::Type{<:Sector}],
              [spin_symmetry::Type{<:Sector}], [lattice::AbstractLattice];
              t, U, mu, n)
```

MPO for the hamiltonian of the Hubbard model, as defined by

$$
H = -t \sum_{\langle i,j \rangle} \sum_{\sigma} \left( e_{i,\sigma}^+ e_{j,\sigma}^- + c_{i,\sigma}^- c_{j,\sigma}^+ \right) + U \sum_i n_{i,\uparrow}n_{i,\downarrow} - \sum_i \mu n_i
$$

where $\sigma$ is a spin index that can take the values $\uparrow$ or $\downarrow$ and $n$ is the fermionic number operator [`e_number`](@ref).

By default, the model is defined on an infinite chain with unit lattice spacing, without any symmetries and with `ComplexF64` entries of the tensors. If the `particle_symmetry` is not `Trivial`, a fixed particle number density `n` can be imposed.
