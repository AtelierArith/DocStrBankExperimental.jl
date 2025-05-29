```
flatmap_parent(f, A)
```

Returns a collection consisting of all elements of each `f(a)`, similar to `flatmap(f, A)`.

Each element of `A` should be a `view` of the same parent array, and these views together should cover all elements of the parent. Elements of the result are in the same order as the corresponding elements in the parent array of `a`s.

# Examples

```
julia> a = [10, 20, 30, 40, 50]

julia> avs = [view(a, [2, 5]), view(a, [3, 1, 4])]
2-element Vector{SubArray{Int64, 1, Vector{Int64}, Tuple{Vector{Int64}}, false}}:
 [20, 50]
 [30, 10, 40]

# multiply by 2 and reassemble in the original order
julia> flatmap_parent(av -> 2 .* av, avs)
5-element Vector{Int64}:
  20
  40
  60
  80
 100
```
