```
RExpr(e::Expr)
```

Convert Julia expression to Reduce expression

## Examples

```julia-repl
julia> RExpr(:(sin(x*im) + cos(y*ϕ)))

     sqrt(5)*y + y
cos(---------------) + sinh(x)*i
           2
```
