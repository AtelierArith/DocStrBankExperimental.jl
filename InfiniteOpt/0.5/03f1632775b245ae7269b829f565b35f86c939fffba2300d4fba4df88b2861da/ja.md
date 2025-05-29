```
JuMP.drop_zeros!(nlp::NLPExpr)::NLPExpr
```

非線形式からゼロ（削除によって導入された可能性がある）を削除します。これはいくつかの単純なヒューリスティックのみを使用しており、`cos(π/2)`のようなより複雑な関係は削除しません。

**例**

```julia-repl
julia> expr = x^2.3 * max(0, zero(NLPExpr)) - exp(1/x + 0)
x^2.3 * max(0, 0) - exp(1 / x + 0)

julia> drop_zeros!(expr)
-exp(1 / x)
```
