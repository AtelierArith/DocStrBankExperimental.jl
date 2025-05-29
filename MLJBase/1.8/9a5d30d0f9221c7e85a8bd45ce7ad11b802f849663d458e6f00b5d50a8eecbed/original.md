```
@node f(...)
```

Construct a new node that applies the function `f` to some combination of nodes, sources and other arguments.

*Important.* An argument not in global scope is assumed to be a node  or source.

### Examples

```julia-repl
julia> X = source(π)
julia> W = @node sin(X)
julia> W()
0

julia> X = source(1:10)
julia> Y = @node selectrows(X, 3:4)
julia> Y()
3:4

julia> Y(["one", "two", "three", "four"])
2-element Array{Symbol,1}:
 "three"
 "four"

julia> X1 = source(4)
julia> X2 = source(5)
julia> add(a, b, c) = a + b + c
julia> N = @node add(X1, 1, X2)
julia> N()
10

```

See also [`node`](@ref)
