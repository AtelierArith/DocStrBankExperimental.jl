```
areaplot([x,] y)
areaplot!([x,] y)
```

Draw a stacked area plot of the matrix y.

# Examples

```julia-repl
julia> areaplot(1:3, [1 2 3; 7 8 9; 4 5 6], seriescolor = [:red :green :blue], fillalpha = [0.2 0.3 0.4])
```
