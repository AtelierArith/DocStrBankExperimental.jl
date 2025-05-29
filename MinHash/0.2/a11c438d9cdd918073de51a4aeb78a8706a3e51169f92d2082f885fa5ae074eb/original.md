```
intersectionlength(y::MinHashSketch, y::MinHashSketch)
```

Count number of hashes in both `x` and `y` more effectively than using ordinary set operations.

# Examples

```julia-repl
julia> x = sketch(1:10000, 100); y = sketch(5000:15000, 100);

julia> intersectionlength(x, y)
49
```
