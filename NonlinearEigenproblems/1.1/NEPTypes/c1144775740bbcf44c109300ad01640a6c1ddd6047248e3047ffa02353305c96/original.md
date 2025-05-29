```
abstract  AbstractSPMF <: ProjectableNEP
```

An AbstractSPMF is an abstract class representing NEPs which can be represented as a sum of products of matrices and functions $M(λ)=Σ_i A_i f_i(λ)$, where i = 0,1,2,..., all of the matrices are of size $n×n$ and $f_i$ are functions.

Any AbstractSPMF has to have implementations of [`get_Av()`](@ref) and [`get_fv()`](@ref) which return the functions and matrices.
