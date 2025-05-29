```
solve(system::SimpleLiquid, closure::Closure, method::Method)
```

Solves the system `system` using the closure `closure` with method `method`.

```
solve(system::SimpleLiquid, closure::Closure)
```

Solves the system `system` using the closure `closure` with the default method `NgIteration()`.
