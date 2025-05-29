```
graphtype{G<:AGraphOrDiGraph}(::Type{G})
```

The graph type corresponding to `G`. If `G<:AGraph` returns `G`, if `G<:ADiGraph` returns a type `H<:AGraph`.
