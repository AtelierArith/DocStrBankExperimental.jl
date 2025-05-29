```
mapleaves(f, [style = WalkStyle], x)
```

Apply `f` to each leaf nodes in `x` and return the result.  `f` only see leaf nodes.

# Example

```julia-repl
julia> mapleaves(x -> @show(x) isa Integer ? x + 1 : x, (a=2, b=(c=4, d=0)))
x = 2
x = 4
x = 0
(a = 3, b = (c = 5, d = 1))

```
