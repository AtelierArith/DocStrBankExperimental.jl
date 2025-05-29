```
struct MixHierarchyDict <: AbstractHierarchyDict
```

An object which contains all dictionaries for mixed (bosonic and fermionic) bath-ADOs hierarchy.

# Fields

  * `idx2nvec` : Return the tuple `(Nvec_b, Nvec_f)` from a given index of ADO, where `b` represents boson and `f` represents fermion
  * `nvec2idx` : Return the index from a given tuple `(Nvec_b, Nvec_f)`, where `b` represents boson and `f` represents fermion
  * `Blvl2idx` : Return the list of ADO-indices from a given bosonic-hierarchy level
  * `Flvl2idx` : Return the list of ADO-indices from a given fermionic-hierarchy level
  * `bosonPtr` : Records the tuple $(\alpha, k)$ for each position in `Nvec_b`, where $\alpha$ and $k$ represents the $k$-th exponential-expansion term of the $\alpha$-th bosonic bath.
  * `fermionPtr` : Records the tuple $(\alpha, k)$ for each position in `Nvec_f`, where $\alpha$ and $k$ represents the $k$-th exponential-expansion term of the $\alpha$-th fermionic bath.
