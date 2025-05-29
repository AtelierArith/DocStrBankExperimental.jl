```
@uninterpreted(f, Int, Bool) # f takes as input IntExpr and returns BoolExpr
@uninterpreted(g, (BitVector, 32), (BitVector, 32)) # g's input and output values are BitVectors of length 32
```

Define an SMT-LIB uninterpreted function. An uninterpreted function can be thought of as an unknown mapping between input and output values. The task of the SMT solver is then to determine whether a mapping exists such that some Boolean statement is true.

For example, we can ask whether there exists a function `f(x)``such that`f(f(x)) == x`,`f(x) == y`and`x != y`.

```julia
@satvariable(x, Bool)
@satvariable(y, Bool)
@uninterpreted(f, Bool, Bool)

status = sat!(distinct(x,y), f(x) == y, f(f(x)) == x, solver=Z3())
println("status = $status")
```
