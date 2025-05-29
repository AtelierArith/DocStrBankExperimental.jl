```
HEOMSuperOp(op, opParity, dims, N; Id_cache=I(N))
```

Construct the HEOM superoperator matrix corresponding to the given system SuperOperator which acts on all `ADOs`.  

During the multiplication on all the `ADOs`, the parity of the output `ADOs` might change depend on the parity of this HEOM superoperator.

# Parameters

  * `op` : The system SuperOperator which will act on all `ADOs`.
  * `opParity::AbstractParity` : the parity label of the given operator (`op`), should be `EVEN` or `ODD`.
  * `dims` : the dimension list of the coupling operator (should be equal to the system `dimensions`).
  * `N::Int` : the number of `ADOs`.
