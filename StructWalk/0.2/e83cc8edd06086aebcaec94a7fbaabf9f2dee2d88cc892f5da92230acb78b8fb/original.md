```
prewalk(f, [style = WalkStyle], x)
```

Apply `f` to each node in `x` and return the result.  `f` sees the node first and then the transformed leaves.

*Notice* that it is possible it walk infinitely if you transform a node into non-leaf value.  Wrapping the non-leaf value with `LeafNode(y)` in `f` to prevent infinite walk.

# Example

```julia-repl
julia> prewalk(x -> @show(x) isa Integer ? x + 1 : x, (a=2, b=(c=4, d=0)))
x = (a = 2, b = (c = 4, d = 0))
x = 2
x = (c = 4, d = 0)
x = 4
x = 0
(a = 3, b = (c = 5, d = 1))

julia> prewalk(x -> @show(x) isa Integer ? x + 1 : x .+ 1, (3, 5))
x = (3, 5)
x = 4
x = 6
(5, 7)

julia> prewalk(x -> @show(x) isa Integer ? StructWalk.LeafNode(x // 2) : x isa Tuple ? =>(x .+ 1...) : x, (3, 5))
x = (3, 5)
x = 4
x = 6
2//1 => 3//1

```

See also: [`postwalk`](@ref), [`LeafNode`](@ref)
