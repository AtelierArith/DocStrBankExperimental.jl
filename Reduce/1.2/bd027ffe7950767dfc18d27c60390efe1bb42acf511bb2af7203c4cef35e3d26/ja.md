```
RExpr(e::Expr)
```

Julia式をReduce式に変換します

## 例

```julia-repl
julia> RExpr(:(sin(x*im) + cos(y*ϕ)))

     sqrt(5)*y + y
cos(---------------) + sinh(x)*i
           2
```
