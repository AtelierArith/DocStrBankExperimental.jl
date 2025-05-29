```
df = xdiff(f; ctx=Dict(), inputs...)
```

Differentiate scalar-valued function w.r.t. its inputs, return derivative function.

```
loss(w, x, y) = sum(w * x .- y)
w = rand(2,3); x = rand(3,4); y = rand(2)
dloss = xdiff(loss; w=w, x=x, y=y)
val, dw, dx, dy = dloss(w, x, y)
```

See also `xgrad()` for a more dynamic API.
