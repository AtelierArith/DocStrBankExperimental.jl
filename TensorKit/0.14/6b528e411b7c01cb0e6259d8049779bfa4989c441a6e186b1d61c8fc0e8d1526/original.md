```
struct FusionTree{I, N, M, L}
```

Represents a fusion tree of sectors of type `I<:Sector`, fusing (or splitting) `N` uncoupled sectors to a coupled sector. It actually represents a splitting tree, but fusion tree is a more common term.

## Fields

  * `uncoupled::NTuple{N,I}`: the uncoupled sectors coming out of the splitting tree, before the possible 𝑍 isomorphism (see `isdual`).
  * `coupled::I`: the coupled sector.
  * `isdual::NTuple{N,Bool}`: indicates whether a 𝑍 isomorphism is present (`true`) or not (`false`) for each uncoupled sector.
  * `innerlines::NTuple{M,I}`: the labels of the `M=max(0, N-2)` inner lines of the splitting tree.
  * `vertices::NTuple{L,Int}`: the integer values of the `L=max(0, N-1)` vertices of the splitting tree. If `FusionStyle(I) isa MultiplicityFreeFusion`, then `vertices` is simply equal to the constant value `ntuple(n->1, L)`.
