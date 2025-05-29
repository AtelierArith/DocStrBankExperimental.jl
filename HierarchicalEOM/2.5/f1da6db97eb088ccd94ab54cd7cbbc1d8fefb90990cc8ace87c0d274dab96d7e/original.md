```
struct HierarchyDict <: AbstractHierarchyDict
```

An object which contains all dictionaries for pure (bosonic or fermionic) bath-ADOs hierarchy.

# Fields

  * `idx2nvec` : Return the `Nvec` from a given index of ADO
  * `nvec2idx` : Return the index of ADO from a given `Nvec`
  * `lvl2idx` : Return the list of ADO-indices from a given hierarchy level
  * `bathPtr` : Records the tuple $(\alpha, k)$ for each position in `Nvec`, where $\alpha$ and $k$ represents the $k$-th exponential-expansion term of the $\alpha$-th bath.
