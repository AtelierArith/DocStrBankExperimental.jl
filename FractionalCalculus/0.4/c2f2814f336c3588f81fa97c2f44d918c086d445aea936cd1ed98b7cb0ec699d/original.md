# Symbolic fractional integral

```
semiint(fun)
```

`semiint` uses SymbolicUtils.jl and Symbolics.jl to compute symbolic fractional integral.

### Example

```julia-repl
julia> using SymbolicUtils
julia> @syms x
julia> semiint(x^4)
0.45851597901024005(x^4.5)
```
