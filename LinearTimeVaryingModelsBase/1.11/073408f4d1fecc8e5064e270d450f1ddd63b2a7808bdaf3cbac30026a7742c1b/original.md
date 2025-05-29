1. Define types that implement the interfaces `AbstractModel` and `AbstractCost`.
2. Create object modelcost = ModelAndCost(model, cost)
3. Run macro @define*modelcost*functions(modelcost). This macro defines the following functions

```
f(x, u, i)  = f(modelcost, x, u, i)
fT(x)       = fT(modelcost, x)
df(x, u, I) = df(modelcost, x, u, I)
```

see also `AbstractModel`, `AbstractCost`
