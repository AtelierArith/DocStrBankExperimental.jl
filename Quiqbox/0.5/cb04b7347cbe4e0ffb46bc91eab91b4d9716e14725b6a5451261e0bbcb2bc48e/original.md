```
flatten(a::Tuple) -> Tuple

flatten(a::AbstractVector) -> AbstractVector
```

Flatten `a::Union{AbstractVector, Tuple}` that contains `AbstractArray`s and/or `Tuple`s.  Only operate on the outermost container.

≡≡≡ Example(s) ≡≡≡

```jldoctest; setup = :(push!(LOAD_PATH, "../../src/"); using Quiqbox)
julia> flatten((:one, 2, [3, 4.0], ([5], "six"), "7"))
(:one, 2, 3.0, 4.0, [5], "six", "7")

julia> flatten([:one, 2, [3, 4.0], ([5], "six"), "7"])
7-element Vector{Any}:
  :one
 2
 3.0
 4.0
  [5]
  "six"
  "7"
```
