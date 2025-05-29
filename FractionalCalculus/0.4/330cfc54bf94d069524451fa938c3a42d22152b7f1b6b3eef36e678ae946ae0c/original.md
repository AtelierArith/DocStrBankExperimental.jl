# Symbolic fractional differentiation

```
semidiff(fun)
```

`semidiff` uses SymbolicUtils.jl and Symbolics.jl to compute symbolic fractional differentiation.

### Example

```julia-repl
julia> using SymbolicUtils
julia> @syms x
julia> semidiff(log(x))
log(4x) / sqrt(πx)
```
