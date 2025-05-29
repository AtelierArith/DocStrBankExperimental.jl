```
abs(a::IntExpr)
```

Return the absolute value of an `IntExpr`.

When called on a `RealExpr`, `abs(a::RealExpr)` returns `ite(a >= 0, a, -a)`. This design decision was made because Z3 allows `abs` to be called on a real-valued expression and returns that result, but `abs` is only defined in the SMT-LIB standard for integer variables. Thus, users may call `abs` on real-valued expressions.
