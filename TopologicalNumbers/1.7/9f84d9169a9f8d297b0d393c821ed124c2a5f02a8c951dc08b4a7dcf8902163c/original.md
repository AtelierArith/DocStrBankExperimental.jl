```
LBFSolution{T1,T2} <: TopologicalNumbersSolutions
```

The `LBFSolution` struct represents a solution for calculating the $k$-local value of Berry flux.

# Fields

  * `TopologicalNumber::T1`: The local Berry flux for each energy bands.
  * `n::T2`: An `AbstractVector` (or a `Tuple`) including two elements of `Int`, which represents wavenumber ($2\pi n/N$) when calculating Berry flux.
