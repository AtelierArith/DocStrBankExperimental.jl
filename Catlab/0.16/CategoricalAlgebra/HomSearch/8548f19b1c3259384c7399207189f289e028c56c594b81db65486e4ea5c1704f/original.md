Find a unique homomorphism between two attributed $C$-sets (subject to a variety of constraints), if one exists.

Returns `nothing` if no homomorphism exists. For many categories $C$, the $C$-set homomorphism problem is NP-complete and thus this procedure generally runs in exponential time. It works best when the domain object is small.

To restrict to *monomorphisms*, or homomorphisms whose components are all injective functions, set the keyword argument `monic=true`. To restrict only certain components to be injective or bijective, use `monic=[...]` or `iso=[...]`. For example, setting `monic=[:V]` for a graph homomorphism ensures that the vertex map is injective but imposes no constraints on the edge map.

To restrict the homomorphism to a given partial assignment, set the keyword argument `initial`. For example, to fix the first source vertex to the third target vertex in a graph homomorphism, set `initial=(V=Dict(1 => 3),)`. Use the keyword argument `type_components` to specify nontrivial components on attribute types for a loose homomorphism. These components must be callable: either Julia functions on the appropriate types or FinFunction(Dict(...)).

Use the keyword argument `alg` to set the homomorphism-finding algorithm. By default, a backtracking search algorithm is used ([`BacktrackingSearch`](@ref)). Use the keyword argument error_failures = true to get errors explaining any immediate inconsistencies in specified initial data.

The keyword `predicates` accepts a Dict{Ob, Dict{Int, Union{Nothing, AbstractVector{Int}}}} For each part of the domain, we have the option to give a constraint as a boolean function of the current assignment and tentative value to assign. E.g. `predicates = (E = Dict(2 => [2,4,6]))` would only find matches which assigned edge#2 to edge #2, #4, or #6 in the codomain.

The keyword `no_bind` can be a boolean (applying to all AttrTypes) or an iterable of specific components: it prevents attribute variables in the domain from being sent to concrete values in the codomain. When the AttrType component is `monic`, it is also the case that attribute variables cannot be sent to concrete values (therefore it is redundant to set `no_bind=true` in such cases). In both of these cases, it's possible to compute homomorphisms when there are "free-floating" attribute variables (which are not referred to by any Attr in the domain), as each such variable has a finite number of possibilities for it to be mapped to.

Setting `any=true` relaxes the constraint that the returned homomorphism is  unique.

See also: [`homomorphisms`](@ref), [`isomorphism`](@ref).
