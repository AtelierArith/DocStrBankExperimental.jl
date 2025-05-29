```
@show_tree(expr, maxdepth=10, linenums=false)
```

shows the tree form of the expression `expr` with maxdepth and prints the line number nodes if `linenums` is true.

## Example

```julia
julia> @show_tree 2x+1
:call
├─ :+
├─ :call
│  ├─ :*
│  ├─ 2
│  └─ :x
└─ 1
```
