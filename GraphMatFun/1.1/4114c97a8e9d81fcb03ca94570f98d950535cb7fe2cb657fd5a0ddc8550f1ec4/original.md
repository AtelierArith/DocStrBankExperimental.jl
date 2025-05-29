```
 (graph,crefs)=graph_monomial_degopt(a; input=:A)
```

Generates the same polynomial as [`graph_monomial`](@ref), in the monomial basis. However, it does so by wrapping a call to [`graph_degopt`](@ref), resulting in more degrees of freedom in `crefs`.
