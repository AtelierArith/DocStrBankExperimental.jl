```
ite(x::BoolExpr, y::AbstractExpr, z::AbstractExpr)
```

if-then-else文。x、y、およびzがBoolの場合、`or(x ∧ y, ¬x ∧ z)`に相当します。yとzは他の式の型である可能性があることに注意してください。たとえば、変数`BoolExpr z`と`IntExpr a`がある場合、Satisfiability.jlは`z + a`を`ite(z, 1, 0) + a`として書き換えます。
