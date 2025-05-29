```
CurlyExpr{FirstArg, E} <: AbstractExpr
```

Matches an expression of the form `FirstArg{args...}`, if `FirstArg` is a `Symbol`, or `args[1]{args[2:end]...}` otherwise.

## Constructors

```
    CurlyExpr{FirstArg, E}(; args::Vector{E}) 
```
