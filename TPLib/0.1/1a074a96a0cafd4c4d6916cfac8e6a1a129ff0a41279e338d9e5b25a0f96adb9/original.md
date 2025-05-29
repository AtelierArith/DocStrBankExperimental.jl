```
compute_halfspaces(M::Matrix{<:SemiRing}, n::Integer)
compute_halfspaces(M::Matrix{<:Number}, n::Integer, semiring=:max)
```

Computes a minimal external representation by means of tropical half-spaces of a tropical cone given by a generating set `M` in dimension `n`, see [4]. The set of generators must be nonempty, ie `M` cannot be empty. It currently handles only the case of generating sets in which every vector has finite entries. Returns a pair `(H::Matrix{<:SemiRing},A::Vector{Vector{Integer}})` where the rows of `H` are the equations for the tropical half-spaces and the vectors of `A` are the sectors of each half-space. 

# References

[1] X. Allamigeon and R.D. Katz. Minimal external representations of tropical polyhedra. Journal of Combinatorial Theory, Series A, 120(4):907–940, 2013.  Eprint arXiv:1205.6314.
