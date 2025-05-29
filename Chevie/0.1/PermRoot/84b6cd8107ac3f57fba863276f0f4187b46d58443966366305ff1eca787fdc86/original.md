`baseX(W::ComplexReflectionGroup)`

returns  as the rows of a matrix a  particular basis of the space `V` where `W` acts: the first `semisimplerank(W)` rows contain the coordinates on the basis of `V` of a basis of the root lattice (given by `simpleroots(W)[independent_roots(W)]`) and the last `rank(W)-semisimplerank(W)` ones contain the same for the orthogonal of the coroots.

When `W` represents a rootdatum for a reductive group, the first lines are the same as `simpleroots(W)`.
