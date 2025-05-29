```
compute_tangent_hypergraph(M::Matrix{<:SemiRing}, P::Vector{<:SemiRing}, n::Integer)
compute_tangent_hypergraph(H::Matrix{<:SemiRing}, A::Vector{Vector{Int64}},  P::Vector{<:SemiRing}, n::Integer) 
compute_tangent_hypergraph(M::Matrix{<:Number}, P::Vector{<:Number}, n::Integer, semiring=:max)
compute_tangent_hypergraph(H::Matrix{<:Number}, A::Vector{Vector{Int64}},  P::Vector{<:Number}, n::Integer, semiring=:max)
```

Computes the tangent directed hypergraph of a point `P` in a tropical cone specified by its generators or inequalities `M` (the difference is made by wether `M` is composed of `n` or `2n` columns) or by halfspaces H with their sectors `A`. Returns the number of vertices of the hypergraph, its hyperedges, and in the case where `M` was specified by inequalities or halfspaces, then the active inequalities or halfspaces associated to the hyperedges. Note that the vertices of the hypergraph are labeled starting at 1, whereas they are labeled starting at 0 in TPLib.

# References

[1] X. Allamigeon. Static analysis of memory manipulations by abstract interpretation – Algorithmics of tropical polyhedra, and application to abstract interpretation. PhD thesis. 

[2] X. Allamigeon, S. Gaubert, E. Goubault. Computing the vertices of tropical polyhedra using directed hypergraphs. Discrete & Computational Geometry, 49(2):247–279, 2013. E-print arXiv:0904.3436v4.
