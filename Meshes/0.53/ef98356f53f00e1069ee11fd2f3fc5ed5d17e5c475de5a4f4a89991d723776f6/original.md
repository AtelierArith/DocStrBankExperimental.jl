```
MinMaxSimplification(method; min=3, max=typemax(Int), maxiter=10)
```

Simplify geometries with binary search algorithm and a parent simplification `method`.

The simplification is performed until the number of vertices is in the `[min, max]` range or until a maximum number of iterations `maxiter` is reached.
