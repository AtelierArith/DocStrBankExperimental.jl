```
MacroCall(; name::Union{Symbol, Expr, GlobalRef}, line::Union{LineNumberNode, NotProvided} = not_provided, args::Vector{Any} = [])
```

Matches a macro call expression. A `MacroCall` object can be applied to one or more expressions, yielding another `MacroCall`. 
