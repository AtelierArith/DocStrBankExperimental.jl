```
RawString(s::AbstractString)
```

Container for directly inserting Asymptote drawing commands

# Examples

```julia-repl
julia> Plot([Circle((0,0),1),RawString2D("draw((0,0)--dir(20));")])
```
