```
to_real(a::IntExpr)
```

Performs manual conversion of an IntExpr to a RealExpr. Note that Satisfiability.jl automatically promotes types in arithmetic and comparison expressions, so this function is usually unnecessary to explicitly call.
