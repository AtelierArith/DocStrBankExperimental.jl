```
symbolic_type(x) = symbolic_type(typeof(x))
symbolic_type(::Type)
```

Get the symbolic type trait of a type. Default to [`NotSymbolic`](@ref) for all types except `Symbol` and `Expr`, both of which are [`ScalarSymbolic`](@ref).

See also: [`ScalarSymbolic`](@ref), [`ArraySymbolic`](@ref), [`NotSymbolic`](@ref)
