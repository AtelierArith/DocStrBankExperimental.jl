```
struct M_Boson_Fermion <: AbstractHEOMLSMatrix
```

HEOM Liouvillian superoperator matrix for mixtured (bosonic and fermionic) bath 

# Fields

  * `data<:AbstractSciMLOperator` : the matrix of HEOM Liouvillian superoperator
  * `Btier` : the tier (cutoff level) for bosonic hierarchy
  * `Ftier` : the tier (cutoff level) for fermionic hierarchy
  * `dimensions` : the dimension list of the coupling operator (should be equal to the system dimensions).
  * `N` : the number of total ADOs
  * `sup_dim` : the dimension of system superoperator
  * `parity` : the parity label of the operator which HEOMLS is acting on (usually `EVEN`, only set as `ODD` for calculating spectrum of fermionic system).
  * `Bbath::Vector{BosonBath}` : the vector which stores all `BosonBath` objects
  * `Fbath::Vector{FermionBath}` : the vector which stores all `FermionBath` objects
  * `hierarchy::MixHierarchyDict`: the object which contains all dictionaries for mixed-bath-ADOs hierarchy.

!!! note "`dims` property"
    For a given `M::M_Boson_Fermion`, `M.dims` or `getproperty(M, :dims)` returns its `dimensions` in the type of integer-vector.

