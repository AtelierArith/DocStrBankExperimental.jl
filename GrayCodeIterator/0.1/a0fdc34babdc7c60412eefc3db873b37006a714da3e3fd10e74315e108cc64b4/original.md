```
GrayCode(n, k [, prefix, mutate = false])
```

Creates an iterator that provides all length `n` and weight `k` binary vectors. Optionally, a prefix vector may be provided and. The items of the iterator are of type `Vector{Int}`.

Setting `mutate = true` causes the vector to mutate in place. This can speed up iteration, however when using this option you should not modify the vector your self. For collect to work properly, mutate must be false (the default).

# Examples

```julia-repl
julia> collect(GrayCode(4,2))
6-element Vector{Vector{Int64}}:
 [0, 0, 1, 1]
 [0, 1, 1, 0]
 [0, 1, 0, 1]
 [1, 1, 0, 0]
 [1, 0, 1, 0]
 [1, 0, 0, 1]
```

```julia-repl
julia> collect(GrayCode(4,2,[1,0]))
2-element Vector{Vector{Int64}}:
 [1, 0, 0, 1]
 [1, 0, 1, 0]
```
