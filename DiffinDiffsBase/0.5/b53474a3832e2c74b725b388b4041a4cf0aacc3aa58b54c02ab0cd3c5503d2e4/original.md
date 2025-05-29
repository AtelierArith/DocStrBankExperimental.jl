```
termset([itr])
termset(ts::Union{Int, Symbol, AbstractTerm}...)
```

Construct a [`TermSet`](@ref) from a collection of terms. Instead of passing an iterable collection, one may pass the terms as arguments directly. In the latter case, any `Int` or `Symbol` will be converted to a `Term`.
