```
RazborovModel{T<:Flag, N, D} <: AbstractFlagModel{T, N, D}
```

A (not fully symmetry reduced) Razborov-style model. If T is an InducedFlag, the hierarchy is the same as the one implemented in Flagmatic. If T is not induced, then a Moebius-transform is applied only on the labeled vertices. The resulting hierarchy is then a basis-transformation of the usual hierarchy, and returns the same bounds, but expressed in non-induced flags.
