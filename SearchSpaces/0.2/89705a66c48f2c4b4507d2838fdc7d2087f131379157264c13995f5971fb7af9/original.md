```
BitArraySpace(;dim)
```

Define a search space delimited by bit arrays.

# Example

```julia-repl
julia> space = BitArraySpace(4)
BitArraySpace(4)

julia> rand(space, 7)
7-element Vector{Vector{Bool}}:
 [0, 1, 1, 0]
 [0, 0, 0, 1]
 [1, 1, 1, 0]
 [0, 0, 0, 1]
 [0, 1, 0, 1]
 [1, 1, 1, 0]
 [1, 0, 0, 0]
```
