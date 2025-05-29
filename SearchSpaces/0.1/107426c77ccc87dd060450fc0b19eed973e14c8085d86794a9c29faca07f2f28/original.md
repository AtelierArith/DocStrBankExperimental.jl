```
PermutationSpace(values; k)
PermutationSpace(k)
```

Define a search space defined by permuting the values of size k (k-permutations).

```julia-repl
julia> space = PermutationSpace([:red, :green, :blue])
PermutationSpace{Vector{Symbol}}([:red, :green, :blue], 3)

julia> rand(space, 5)
5-element Vector{Vector{Symbol}}:
 [:blue, :green, :red]
 [:red, :blue, :green]
 [:blue, :green, :red]
 [:green, :blue, :red]
 [:red, :blue, :green]

julia> Grid(PermutationSpace(3)) |> collect
6-element Vector{Any}:
 [1, 2, 3]
 [1, 3, 2]
 [2, 1, 3]
 [2, 3, 1]
 [3, 1, 2]
 [3, 2, 1]
```
