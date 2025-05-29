```
Bindings(; refs = Dict{Symbol,Any}(), funcs = Dict{Symbol,Any}(), warn_override = true)
```

Structure holding information about bindings which either act as references (simple substitutions) or as functions, which can be called with arguments. This allows a small domain-specific language to be used when constructing algebraic expressions.

References are `lhs::Symbol => rhs` pairs where the left-hand side simply expands to the right-hand side during parsing. Right-hand sides which include `lhs` are supported, such that references of the form `x = x::Vector` are allowed, but will be expanded only once. Functions are `name::Symbol => body` pairs where `rhs` must refer to their arguments with `Expr(:argument, <literal::Int>)` expressions. Recursion is not supported and will lead to a `StackOverflowError`. See [`@arg`](@ref).

Most default functions and symbols are implemented using this mechanism. If `warn_override` is set to true, overrides of such default functions will trigger a warning.
