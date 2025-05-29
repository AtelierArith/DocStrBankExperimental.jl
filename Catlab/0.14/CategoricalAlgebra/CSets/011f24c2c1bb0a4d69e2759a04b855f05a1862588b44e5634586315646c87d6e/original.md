Find a homomorphism between two attributed $C$-sets.

Returns `nothing` if no homomorphism exists. For many categories $C$, the $C$-set homomorphism problem is NP-complete and thus this procedure generally runs in exponential time. It works best when the domain object is small.

To restrict to *monomorphisms*, or homomorphisms whose components are all injective functions, set the keyword argument `monic=true`. To restrict only certain components to be injective or bijective, use `monic=[...]` or `iso=[...]`. For example, setting `monic=[:V]` for a graph homomorphism ensures that the vertex map is injective but imposes no constraints on the edge map.

To restrict the homomorphism to a given partial assignment, set the keyword argument `initial`. For example, to fix the first source vertex to the third target vertex in a graph homomorphism, set `initial=(V=Dict(1 => 3),)`.

Use the keyword argument `alg` to set the homomorphism-finding algorithm. By default, a backtracking search algorithm is used ([`BacktrackingSearch`](@ref)).

See also: [`homomorphisms`](@ref), [`isomorphism`](@ref).
