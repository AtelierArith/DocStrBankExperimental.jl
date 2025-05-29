```
prime_decomposition_type(O::AbsSimpleNumFieldOrder, p::Integer) -> Vector{Tuple{Int, Int}}
```

Returns an array of tuples whose length is the number of primes lying over $p$ and the $i$-th tuple gives the splitting type of the corresponding prime, ordered as inertia degree and ramification index.
