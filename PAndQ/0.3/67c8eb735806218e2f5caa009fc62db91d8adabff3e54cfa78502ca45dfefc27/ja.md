```
disjunction(ps)
⋁(ps)
```

`fold(𝒾, (∨) => ps` と同等です。

`⋁` は `\bigvee[TAB]` で入力できます。

[`identical`](@ref)、[`or`](@ref)、および [`fold`](@ref) も参照してください。

# 例

```jldoctest
julia> ⋁(())
⊥

julia> @atomize ⋁((p, q, r, s))
((p ∨ q) ∨ r) ∨ s
```
