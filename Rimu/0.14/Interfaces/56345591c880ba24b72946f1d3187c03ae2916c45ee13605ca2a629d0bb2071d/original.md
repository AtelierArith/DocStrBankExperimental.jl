```
apply_column!(v, op, addr, num, boost=1) -> stats::Tuple
```

Apply the product of column `addr` of the operator `op` and the scalar `num` to the vector `v` according to the [`StochasticStyle`](@ref) of `v`. By expectation value this should be equivalent to

```
v .+= op[:, add] .* num
```

This is used to perform the spawning step in FCIQMC and to implement operator-vector multiplications. Mutates `v` and reports spawning statistics.

The `boost` argument multiplicatively increases the number of spawns to be performed without affecting the expectation value of the procedure.
