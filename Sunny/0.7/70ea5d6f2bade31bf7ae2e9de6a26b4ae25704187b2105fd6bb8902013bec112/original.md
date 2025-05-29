```
enable_dipole_dipole!(sys::System, μ0_μB²)
```

Enables long-range interactions between magnetic dipole moments,

$$
    -(μ_0/4π) ∑_{⟨ij⟩}  [3 (μ_i⋅𝐫̂_{ij})(μ_j⋅𝐫̂_{ij}) - μ_i⋅μ_j] / r_{ij}^3,
$$

where the sum is over all pairs of sites (singly counted), including periodic images, regularized using the Ewald summation convention. Each magnetic moment is $μ = -g μ_B 𝐒$, where $𝐒$ is the spin angular momentum dipole. The parameter `μ0_μB²` specifies the physical constant $μ_0 μ_B^2$, which has dimensions of length³-energy. Obtain this constant for a given system of [`Units`](@ref) via its `vacuum_permeability` property.

# Example

```julia
units = Units(:meV, :angstrom)
enable_dipole_dipole!(sys, units.vacuum_permeability)
```

!!! tip "Efficiency considerations"
    Dipole-dipole interactions are very efficient in the context of spin dynamics simulation, e.g. [`Langevin`](@ref). Sunny applies the fast Fourier transform (FFT) to spins on each Bravais sublattice, such that the computational cost to integrate one time-step scales like $M^2 N \ln N$, where $N$ is the number of cells in the system and $M$ is the number of Bravais sublattices per cell. Conversely, dipole-dipole interactions are highly *inefficient* in the context of a [`LocalSampler`](@ref). Each Monte Carlo update of a single spin currently requires scanning over all other spins in the system.


See also [`modify_exchange_with_truncated_dipole_dipole!`](@ref).
