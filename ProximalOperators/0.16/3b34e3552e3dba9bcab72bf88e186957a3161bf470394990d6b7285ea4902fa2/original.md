```
Regularize(f, ρ=1.0, a=0.0)
```

Given function `f`, and optional parameters `ρ` (positive) and `a`, return

$$
g(x) = f(x) + \tfrac{ρ}{2}\|x-a\|².
$$

Parameter `a` can be either an array or a scalar, in which case it is subtracted component-wise from `x` in the above expression.
