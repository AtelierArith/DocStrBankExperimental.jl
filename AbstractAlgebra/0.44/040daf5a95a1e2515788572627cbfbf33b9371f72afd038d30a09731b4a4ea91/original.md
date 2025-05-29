```
laurent_polynomial_ring(R::Ring, varnames...; cached::Bool = true)
```

Given a base ring `R` and variable names `varnames...`, say `:x, :y, :z`, return a tuple `S, x, y, z` representing the new ring $S = R[x, 1/x, y, 1/y, z, 1/z]$ and the generators $x, y, z$ of the ring.

By default (`cached=true`), the output `S` will be cached, i.e. if `laurent_polynomial_ring` is invoked again with the same arguments, the same (*identical*) ring is returned. Setting `cached` to `false` ensures a distinct new ring is returned, and will also prevent it from being cached.

For information about the many ways to specify `varnames...` refer to [`polynomial_ring`](@ref) or the specification in [`AbstractAlgebra.@varnames_interface`](@ref).
