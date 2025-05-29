```
struct M_S <: AbstractHEOMLSMatrix
```

HEOM Liouvillian superoperator matrix with cutoff level of the hierarchy equals to `0`.   This corresponds to the standard Schrodinger (Liouville-von Neumann) equation, namely

$$
M[\cdot]=-i \left[H_{sys}, \cdot \right]_-,
$$

where $[\cdot, \cdot]_-$ stands for commutator.

# Fields

  * `data<:AbstractSciMLOperator` : the matrix of HEOM Liouvillian superoperator
  * `tier` : the tier (cutoff level) for the hierarchy, which equals to `0` in this case
  * `dimensions` : the dimension list of the coupling operator (should be equal to the system dimensions).
  * `N` : the number of total ADOs, which equals to `1` (only the reduced density operator) in this case
  * `sup_dim` : the dimension of system superoperator
  * `parity` : the parity label of the operator which HEOMLS is acting on (usually `EVEN`, only set as `ODD` for calculating spectrum of fermionic system).

!!! note "`dims` property"
    For a given `M::M_S`, `M.dims` or `getproperty(M, :dims)` returns its `dimensions` in the type of integer-vector.

