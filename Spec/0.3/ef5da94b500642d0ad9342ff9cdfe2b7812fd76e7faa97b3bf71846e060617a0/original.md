`specapply(f, args...)`

Evaluate `f(args...)` and check pre and post conditions of all functions encountered.

```
f(x) = abs(x)
@post f(ret, x) = x > 0)
specapply(f, 0.3)
```
