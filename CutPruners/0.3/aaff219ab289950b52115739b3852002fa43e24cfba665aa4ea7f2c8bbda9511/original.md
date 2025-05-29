A cut pruner maintains a matrix `A` and a vector `b` such that represents `size(A, 1)` (`== length(b)`) cuts. Let `a_i` be `-A[i,:]` if `lazy_minus` and `A[i,:]` otherwise and `β_i` be `b[i]`, the meaning of the cut depends on the sense. If `sense` is

  * `:Min`, then the cut pruner represents the concave polyhedral function `min ⟨a_i, x⟩ + β_i`;
  * `:Max`, then the cut pruner represents the convex polyhedral function `max ⟨a_i, x⟩ + β_i`;
  * `:≤`, then the cut pruner represents the polyhedra defined by the intersection of the half-space `⟨a_i, x⟩ ≤ β_i`;
  * `:≥`, then the cut pruner represents the polyhedra defined by the intersection of the half-space `⟨a_i, x⟩ ≥ β_i`.

Internally, instead of `sense`, the booleans `isfun` and `islb` are stored. The mapping between `sense` and these two booleans is given by the following table

| `sense` | `isfun` | `islb` |
| -------:| -------:| ------:|
|     Min |    true |  false |
|     Max |    true |   true |
|       ≤ |   false |  false |
|       ≥ |   false |   true |
