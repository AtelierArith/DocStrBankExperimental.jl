```
conjugacy_relations(gr::GroupRelationGraph, sgnumᴳ, sgnumᴴ) --> Vector{<:ConjugacyTransform}
```

Given a graph `gr` representing a sub- or supergroup relation, return the possible transformations that make up the conjugacy classes between the groups `sgnumᴳ` and `sgnumᴴ`.

The returned transforms `ts` bring `G` into the setting of `H` via `transform.(G, Ref(t.P), Ref(t.p))`, where `t` is an element of `ts`, i.e., one possible conjugacy transform, and `t.P` and `t.p` denote the associated transform's rotation and translation, respectively. 

Note that the transforms need not preserve volume: accordingly, some operations may be redundant after transformation (use [`reduce_ops`](@ref) or `unique!` to remove these).

## Example

Consider the following example, which looks at the subgroup relationship between space groups ⋕168 and ⋕3:

```jldoctest conjugacy_relation
julia> gr = maximal_subgroups(168)
GroupRelationGraph (subgroups) of SpaceGroup{3} ⋕168 with 4 vertices:
 ⋕168
 ├─►⋕143ᵀ (index 2)  ╌╌►⋕1ᵀ (index 3)
 └─►⋕3ᵀ (index 3)  ╌╌►⋕1ᵀ (index 2)

julia> sg168 = spacegroup(168)
SpaceGroup{3} ⋕168 (P6) with 6 operations:
 1
 3₀₀₁⁺
 3₀₀₁⁻
 2₀₀₁
 6₀₀₁⁻
 6₀₀₁⁺

julia> sg3 = spacegroup(3)
SpaceGroup{3} ⋕3 (P2) with 2 operations:
 1
 2₀₁₀
```

Note that the symmetry operation 2₀₁₀ (from ⋕3) and 2₀₀₁ (from ⋕168) differ by a transformation; even though they are isomorphic, this is not clearly reflected because they are in different settings. We can use `conjugacy_relations` to find the transformations that brings ⋕168 into the setting of ⋕3:

```jldoctest conjugacy_relation
julia> ts = conjugacy_relations(gr, 168, 3) # possible transforms from ⋕168 to ⋕3
1-element Vector{Crystalline.ConjugacyTransform{3}}:
 P = [0 0 1; 1 0 0; 0 1 0]

julia> sg168′ = transform.(sg168, Ref(ts[1].P), Ref(ts[1].p))
6-element Vector{SymOperation{3}}:
 1
 3₀₁₀⁺
 3₀₁₀⁻
 2₀₁₀
 6₀₁₀⁻
 6₀₁₀⁺

julia> issubgroup(sg168, sg3) # not identified as subgroup, since settings differ
false

julia> issubgroup(sg168′, sg3) # settings now agree, and subgroup relationship is evident
true
```

Here, there is only one possible transformation: in general, however, there may be many.
