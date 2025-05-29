addLasserreBlock!(m::FlagModel{T,N,D}, maxEdges::Int; maxVertices = maxEdges * maxPredicateArguments(T)) where {T<:Flag,N,D}

Adds a symmetry reduced Lasserre block of internal flag type 'T' to 'm' and returns it. All flags with up to 'floor(maxEdges/2)' edges (resp. true predicates) with optionally at most 'floor(maxVertices/2)' vertices are added as generators of the block. The resulting hierarchy contains flags with at most 'maxEdges' edges and 'maxVertices' vertices.
