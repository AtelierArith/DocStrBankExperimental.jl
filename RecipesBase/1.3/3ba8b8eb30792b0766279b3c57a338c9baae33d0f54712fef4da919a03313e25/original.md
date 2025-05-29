```
@layout mat
```

Generate the subplots layout from a matrix of symbols (where subplots can span multiple rows or columns). Precise sizing can be achieved with curly brackets, otherwise the free space is equally split between the plot areas of subplots. You can use the `_` character (underscore) to ignore plots in the layout (blank plots).

# Examples

```julia-repl
julia> @layout [a b; c]
2×1 Matrix{Any}:
 Any[(label = :a, blank = false) (label = :b, blank = false)]
 (label = :c, blank = false)

julia> @layout [a{0.3w}; b{0.2h}]
2×1 Matrix{Any}:
 (label = :a, width = 0.3, height = :auto)
 (label = :b, width = :auto, height = 0.2)

julia> @layout [_ ° _; ° ° °; ° ° °]
3×3 Matrix{Any}:
 (label = :_, blank = true)   …  (label = :_, blank = true)
 (label = :°, blank = false)     (label = :°, blank = false)
 (label = :°, blank = false)     (label = :°, blank = false)

```
