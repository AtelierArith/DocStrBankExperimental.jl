```
struct GlobalRel <: AbstractRelation end;
const globalrel  = GlobalRel();
```

Singleton type for the global relation. This is a binary relation via which a world accesses every other world within the frame. The relation is also symmetric, reflexive and transitive.

# Examples

```julia-repl
julia> syntaxstring(SoleLogics.globalrel)
"G"

julia> SoleLogics.converse(globalrel)
GlobalRel()
```

See also [`identityrel`](@ref), [`AbstractRelation`](@ref), [`AbstractWorld`](@ref), [`AbstractFrame`](@ref). [`AbstractKripkeStructure`](@ref),
