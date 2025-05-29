```
columntable(s::OptSummary, [stack::Bool=false])
```

Return `s.fitlog` as a `Tables.columntable`.

When `stack` is false (the default), there will be 3 columns in the result:

  * `iter`: the iteration number
  * `objective`: the value of the objective at that sample
  * `θ`: the parameter vector at that sample

When `stack` is true, there will be 4 columns: `iter`, `objective`, `par`, and `value` where `value` is the stacked contents of the `θ` vectors (the equivalent of `vcat(θ...)`) and `par` is a vector of parameter numbers.
