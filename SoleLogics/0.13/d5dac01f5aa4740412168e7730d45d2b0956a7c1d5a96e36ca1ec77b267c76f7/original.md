```
struct IdentityRel <: AbstractRelation end;
const identityrel   = IdentityRel();
```

Singleton type for the identity relation. This is a binary relation via which a world accesses itself. The relation is also symmetric, reflexive and transitive.

# Examples

```julia-repl
julia> syntaxstring(SoleLogics.identityrel)
"="

julia> SoleLogics.converse(identityrel)
IdentityRel()
```

See also [`globalrel`](@ref), [`AbstractRelation`](@ref), [`AbstractWorld`](@ref), [`AbstractFrame`](@ref). [`AbstractKripkeStructure`](@ref),
