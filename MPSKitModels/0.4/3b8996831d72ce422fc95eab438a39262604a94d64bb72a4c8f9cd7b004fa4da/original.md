```
bilinear_biquadratic_model([elt::Type{<:Number}], [symmetry::Type{<:Sector}],
                           [lattice::AbstractLattice]; spin=1, J=1.0, θ=0.0)
```

MPO for the hamiltonian of the bilinear biquadratic Heisenberg model, as defined by

$$
H = J \sum_{\langle i,j \rangle} \left(\cos(\theta) \vec{S}_i \cdot \vec{S}_j + \sin(\theta) \left( \vec{S}_i \cdot \vec{S}_j \right)^2 \right)
$$

where $\vec{S} = (S^x, S^y, S^z)$.

By default, the model is defined on an infinite chain with unit lattice spacing, without any symmetries and with `ComplexF64` entries of the tensors.
