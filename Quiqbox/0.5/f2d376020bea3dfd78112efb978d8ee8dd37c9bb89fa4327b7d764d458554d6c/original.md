```
getUnique!(arr::AbstractVector, args...; compareFunction::Function = hasEqual, 
           kws...) -> 
AbstractVector
```

Similar to [`markUnique`](@ref) but instead, directly return the modified `arr` so that the  repeated entries are deleted.

≡≡≡ Example(s) ≡≡≡

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
