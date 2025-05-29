```
connected_mcis(mol1::MolGraph, mol2::MolGraph; kwargs...) -> (Dict, Symbol)
connected_mces(mol1::MolGraph, mol2::MolGraph; kwargs...) -> (Dict, Symbol)
```

Compute connected maximum common substructure (MCS) of mol1 and mol2.

## Keyword arguments

  * timeout(Real): abort calculation and return suboptimal results if the execution

time has reached the given value (default=60, in seconds).

  * targetsize(Int): abort calculation and return suboptimal result so far if the

given mcs size achieved.
