```
getUnique!(arr::AbstractVector, args...; compareFunction::Function = hasEqual, 
           kws...) -> 
AbstractVector
```

[`markUnique`](@ref)と似ていますが、重複したエントリが削除されるように、修正された`arr`を直接返します。

≡≡≡ 例 ≡≡≡

```jldoctest; setup = :(push!(LOAD_PATH, "../../src/"); using Quiqbox)
julia> arr = [1, [1, 2],"s", [1, 2]]
4-element Vector{Any}:
 1
  [1, 2]
  "s"
  [1, 2]

julia> getUnique!(arr);

julia> arr
3-element Vector{Any}:
 1
  [1, 2]
  "s"
```
