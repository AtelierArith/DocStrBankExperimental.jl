```
InplaceBatchIntegralFunction(f!, prototype; max_batch::Integer=typemax(Int))
```

Constructor for an inplace, batched integrand of the form `f!(y, x, p)` that accepts an array `x` containing a batch of evaluation points stored along the last axis of the array. A `prototype` array is required to store the same type and size as the result, `y`, however the last axis, which is reserved for batching, which should contain at least one element. The `max_batch` keyword sets a soft limit on the number of points batched simultaneously.
