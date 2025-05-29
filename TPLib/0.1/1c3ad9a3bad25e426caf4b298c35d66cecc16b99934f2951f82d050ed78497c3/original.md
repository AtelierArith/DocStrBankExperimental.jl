```
compute_tropical_complex(M::Matrix{<:SemiRing}, n::Integer)
compute_tropical_complex(M::Matrix{<:Number}, n::Integer, semiring=:max)
```

Computes the tropical complex associated with a tropical cone given by a generating set. Only generating sets which are minimal and in which every vector has finite entries are supported. Returns a pair `(V::Matrix{<:Number},A::Vector{Vector{Int64}})` where the rows of `V` are the vertices of the complex, and `A` is the collection of maximal cells (defined by adjacency with vertices). Note that each cell is seen as a usual polytope, and not as a tropical one, and that the vertices are not necessarily unique.

# References

[1] M. Develin and B. Sturmfels. Tropical convexity. Doc. Math., 9:1–27 (electronic), 2004. E-print arXiv:math.MG/0308254.
