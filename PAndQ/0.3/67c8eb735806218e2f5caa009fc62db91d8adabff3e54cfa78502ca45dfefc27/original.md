```
disjunction(ps)
⋁(ps)
```

Equivalent to `fold(𝒾, (∨) => ps)`.

`⋁` can be typed by `\bigvee[TAB]`.

See also [`identical`](@ref), [`or`](@ref), and [`fold`](@ref).

# Examples

```jldoctest
julia> ⋁(())
⊥

julia> @atomize ⋁((p, q, r, s))
((p ∨ q) ∨ r) ∨ s
```
