```
addTerminator(M, Bath)
```

Adding terminator to a given HEOMLS matrix.

The terminator is a Liouvillian term representing the contribution to  the system-bath dynamics of all exponential-expansion terms beyond `Bath.Nterm`

The difference between the true correlation function and the sum of the  `Bath.Nterm`-exponential terms is approximately `2 * δ * dirac(t)`. Here, `δ` is the approximation discrepancy and `dirac(t)` denotes the Dirac-delta function.

# Parameters

  * `M::AbstractHEOMLSMatrix` : the matrix given from HEOM model
  * `Bath::Union{BosonBath, FermionBath}` : The bath object which contains the approximation discrepancy δ

# Return

  * `M_new::AbstractHEOMLSMatrix` : the new HEOM Liouvillian superoperator matrix
