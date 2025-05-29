```
ModulatedFourierLattice{D} <: AbstractFourierLattice{D}
```

A `D`-dimensional concrete Fourier (plane wave) lattice, derived from  a [`UnityFourierLattice{D}`](@ref) by scaling and modulating its orbit coefficients  by complex numbers; in general, the coefficients do not have unit norm.
