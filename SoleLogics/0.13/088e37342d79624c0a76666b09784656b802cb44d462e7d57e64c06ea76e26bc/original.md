```
struct DiamondRelationalConnective{R<:AbstractRelation} <: AbstractRelationalConnective{R} end
struct BoxRelationalConnective{R<:AbstractRelation} <: AbstractRelationalConnective{R} end
```

Singleton types for relational connectives, typically interpreted as the modal existential and universal quantifier, respectively.

Both connectives can be easily instantiated with relation instances, such as `DiamondRelationalConnective(rel)`, which is a shortcut for `DiamondRelationalConnective{typeof(rel)}()`.

# Examples

```julia-repl
julia> syntaxstring(DiamondRelationalConnective(IA_A))
"⟨A⟩"

julia> syntaxstring(BoxRelationalConnective(IA_A))
"[A]"

julia> @assert DiamondRelationalConnective(IA_A) == SoleLogics.dual(BoxRelationalConnective(IA_A))

```

See also [`DiamondRelationalConnective`](@ref), [`BoxRelationalConnective`](@ref), [`syntaxstring`](@ref), [`dual`](@ref), [`AbstractKripkeStructure`](@ref), [`AbstractFrame`](@ref).
