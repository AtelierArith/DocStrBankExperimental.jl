```
SpinWaveTheory(sys::System; measure, regularization=1e-8)
```

Constructs an object to perform linear spin wave theory. The system must be in an energy minimizing configuration. Enables calculation of [`dispersion`](@ref) bands. If pair correlations are specified with `correspec`, one can also calculate [`intensities_bands`](@ref) and broadened [`intensities`](@ref).

The spins in system must be energy-minimized, otherwise the Cholesky step of the Bogoliubov diagonalization procedure will fail. The parameter `regularization` adds a small positive shift to the diagonal of the dynamical matrix to avoid numerical issues with quasi-particle modes of vanishing energy. Physically, this shift can be interpreted as application of an inhomogeneous field aligned with the magnetic ordering.
