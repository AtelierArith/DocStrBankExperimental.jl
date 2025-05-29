```
refvalue(A, x)
```

For the *original* array `A`, and a "ref value" `x` taken from `refarray(A)`, return the appropriate *original* value. `refvalue(A, refarray(A)[I...])` must be equal to `A[I...]`.

By default, `refvalue(A, x)` returns `x` (since `refarray(A)` returns `A` by default). This allows recovering an original array element after operating on the "ref values".

This generic function is owned by DataAPI.jl itself, which is the sole provider of the default definition.
