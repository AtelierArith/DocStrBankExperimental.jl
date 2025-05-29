```
xdiff(ex; ctx=Dict(), inputs...)
```

Differentiate scalar-valued expression w.r.t. its inputs, return expression for the derivatives.

```
ex = :(sum(w * x .- y))
dex = xdiff(ex; w=rand(2,3), x=rand(3,4), y=rand(2))
```

`xdiff()` also accepts a context `ctx::Dict{Any,Any}` which can be used to pass options and extract additional information. Some options include:

  * `codegen::Espresso.CodeGen` - code generator used for derivative expression;                               valid values include `VecotorCodeGen()`, `BufCodeGen()`                               and `CuCodeGen()`
