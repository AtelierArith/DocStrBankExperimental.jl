```
slice(F::System, L::LinearSubspace; compile = mixed)
slice(F::AbstractSystem, L::LinearSubspace)
```

Slice the zero set of the polynomial system `F` with the affine linear subspace `L` defined by $Ax = b$. This constructs the system `[F(x); A x - b] = 0`. See also [`SlicedSystem`](@ref).
