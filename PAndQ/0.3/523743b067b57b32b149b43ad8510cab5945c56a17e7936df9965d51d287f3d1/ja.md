```
conjunction(ps)
⋀(ps)
```

`fold(𝒾, (∧) => ps)`に相当します。

`⋀`は`\bigwedge[TAB]`で入力できます。

[`identical`](@ref)、[`and`](@ref)、および[`fold`](@ref)も参照してください。

# 例

```jldoctest
julia> ⋀(())
⊤

julia> @atomize ⋀((p, q, r, s))
((p ∧ q) ∧ r) ∧ s
```
