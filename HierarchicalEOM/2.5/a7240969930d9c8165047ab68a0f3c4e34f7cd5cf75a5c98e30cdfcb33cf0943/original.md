```
struct M_Boson <: AbstractHEOMLSMatrix
```

HEOM Liouvillian superoperator matrix for bosonic bath

# Fields

  * `data<:AbstractSciMLOperator` : the matrix of HEOM Liouvillian superoperator
  * `tier` : the tier (cutoff level) for the bosonic hierarchy
  * `dimensions` : the dimension list of the coupling operator (should be equal to the system dimensions).
  * `N` : the number of total ADOs
  * `sup_dim` : the dimension of system superoperator
  * `parity` : the parity label of the operator which HEOMLS is acting on (usually `EVEN`, only set as `ODD` for calculating spectrum of fermionic system).
  * `bath::Vector{BosonBath}` : the vector which stores all `BosonBath` objects
  * `hierarchy::HierarchyDict`: the object which contains all dictionaries for boson-bath-ADOs hierarchy.

!!! note "`dims` property"
    For a given `M::M_Boson`, `M.dims` or `getproperty(M, :dims)` returns its `dimensions` in the type of integer-vector.

