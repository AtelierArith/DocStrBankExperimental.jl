```
annotate!(anns)
annotate!(anns::Tuple...)
annotate!(x, y, txt)
```

Add annotations to an existing plot. Annotations are specified either as a vector of tuples, each of the form `(x,y,txt)`, or as three vectors, `x, y, txt`. Each `txt` can be a `String`, `PlotText` PlotText (created with `text(args...)`), or a tuple of arguments to `text` (e.g., `("Label", 8, :red, :top)`).

# Example

```julia-repl
julia> plot(1:10)
julia> annotate!([(7,3,"(7,3)"),(3,7,text("hey", 14, :left, :top, :green))])
julia> annotate!([(4, 4, ("More text", 8, 45.0, :bottom, :red))])
julia> annotate!([2,5], [6,3], ["text at (2,6)", "text at (5,3)"])
```
