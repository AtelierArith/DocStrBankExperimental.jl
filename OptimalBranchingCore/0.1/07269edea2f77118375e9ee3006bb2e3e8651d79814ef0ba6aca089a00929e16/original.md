```
reduce_problem(::Type{R}, problem::AbstractProblem, reducer::AbstractReducer) where R
```

Reduces the problem size directly, e.g. by graph rewriting. It is a crucial step in the reduce and branch strategy.

### Arguments

  * `R`: The element type used for computing the size of solution. The should have an additive commutative monoid structure.
  * `problem`: The problem instance.
  * `reducer`: The reducer.

### Returns

A tuple of two values:

  * `AbstractProblem`: A new instance of `AbstractProblem` with reduced size.
  * `Number`: The local gain of the reduction, which will be added to the global gain.
