`mappingPerm([::Type{T},]a::AbstractVector{<:Integer})`

given  a list  of positive  integers without  repetition `a`, this function finds  a  `Perm{T}`  `p`  such  that  `sort(a).^p==a`.  This can be used to translate  between arrangements and `Perm`s. If  omitted `T` is taken to be `Int16`.

```julia-repl
julia> p=mappingPerm([6,7,5])
(5,6,7)

julia> (5:7).^p
3-element Vector{Int64}:
 6
 7
 5
```
