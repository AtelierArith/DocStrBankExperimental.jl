```
Bodies(bodies, ops::AbstractVector)
```

  * `bodies::Vector{AutoBody}`: Vector of `AutoBody`
  * `ops::Vector{Function}`: Vector of operators for the superposition of multiple `AutoBody`s

Superposes multiple `body::AutoBody` objects together according to the operators `ops`. While this can be manually performed by the operators implemented for `AutoBody`, adding too many bodies can yield a recursion problem of the `sdf` and `map` functions not fitting in the stack. This type implements the superposition of bodies by iteration instead of recursion, and the reduction of the `sdf` and `map` functions is done on the `mesure` function, and not before. The operators vector `ops` specifies the operation to call between two consecutive `AutoBody`s in the `bodies` vector. Note that `+` (or the alias `∪`) is the only operation supported between `Bodies`.
