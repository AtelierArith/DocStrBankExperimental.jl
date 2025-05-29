```
violin(x,y,z)
violin!(x,y,z)
```

Make a violin plot.

# Example

```julia-repl
julia> violin(repeat([1,2,3],outer=100),randn(300))
```
