```
SymmetricBZ(A, B, lims::AbstractIteratedLimits, syms; atol=sqrt(eps()))
```

Data type representing a Brillouin zone reduced by a set of symmetries, `syms` with iterated integration limits `lims`, both of which are assumed to be in the lattice basis (since the Fourier series is). `A` and `B` should be identically-sized square matrices containing the real and reciprocal basis vectors in their columns.

!!! note "Convention"
    This type assumes all integration limit data is in the reciprocal lattice basis with fractional coordinates, where the FBZ is just the hypercube spanned by the vertices (0,…,0) & (1,…,1). If necessary, use `A` or `B` to rotate these quantities into the convention.


`lims` should be limits compatible with [IteratedIntegration.jl](https://github.com/lxvm/IteratedIntegration.jl). `syms` should be an iterable collection of point group symmetries compatible with [AutoSymPTR.jl](https://github.com/lxvm/AutoSymPTR.jl).
