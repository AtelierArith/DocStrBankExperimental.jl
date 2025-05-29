```
SlicedSystem(F::AbstractSystem, L::LinearSubspace)
```

Given a polynomial system `F` with the affine linear subspace `L` defined by $Ax = b$ this constructs the system `[F(x); A x - b] = 0`. See also [`slice`](@ref).
