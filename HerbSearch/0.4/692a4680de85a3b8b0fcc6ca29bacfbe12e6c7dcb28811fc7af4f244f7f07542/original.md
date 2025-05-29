```
rand(::Type{RuleNode}, grammar::AbstractGrammar, typ::Symbol, dmap::AbstractVector{Int}, max_depth::Int=10)
```

Generates a random [`RuleNode`](@ref), i.e. an expression tree, of root type typ and maximum depth max_depth guided by a depth map dmap if possible.
