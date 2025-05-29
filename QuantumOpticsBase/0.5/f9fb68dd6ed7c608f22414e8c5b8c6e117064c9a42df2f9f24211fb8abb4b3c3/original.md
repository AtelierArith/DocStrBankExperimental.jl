```
LazySum([Tf,] [factors,] operators)
LazySum([Tf,] basis_l, basis_r, [factors,] [operators])
LazySum(::Tuple, x::LazySum)
```

Lazy evaluation of sums of operators.

All operators have to be given in respect to the same bases. The field `factors` accounts for an additional multiplicative factor for each operator stored in the `operators` field.

The factor type `Tf` can be specified to avoid having to infer it from the factors and operators themselves. All `factors` will be converted to type `Tf`.

The `operators` will be kept as is. It can be, for example, a `Tuple` or a `Vector` of operators. Using a `Tuple` is recommended for runtime performance of operator-state operations, such as simulating time evolution. A `Vector` can reduce compile-time overhead when doing arithmetic on `LazySum`s, such as summing many `LazySum`s together.

To convert a vector-based `LazySum` `x` to use a tuple for operator storage, use `LazySum(::Tuple, x)`. 
