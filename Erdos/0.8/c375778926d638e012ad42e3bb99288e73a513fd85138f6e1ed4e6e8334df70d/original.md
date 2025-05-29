```
digraphtype{G<:AGraphOrDiGraph}(::Type{G})
```

The digraph type corresponding to `G`. If `G<:ADiGraph` returns `G`, if `G<:AGraph` returns a type `H<:ADiGraph`.
