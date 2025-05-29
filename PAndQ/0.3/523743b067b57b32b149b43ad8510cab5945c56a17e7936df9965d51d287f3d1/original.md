```
conjunction(ps)
⋀(ps)
```

Equivalent to `fold(𝒾, (∧) => ps)`.

`⋀` can be typed by `\bigwedge[TAB]`.

See also [`identical`](@ref), [`and`](@ref), and [`fold`](@ref).

# Examples

```jldoctest
julia> ⋀(())
⊤

julia> @atomize ⋀((p, q, r, s))
((p ∧ q) ∧ r) ∧ s
```
