```
evaluate(m, x)
```

Evaluates the `TPS` function `m` at the result `x`.

# Arguments

  * `m::Union{TPS,AbstractArray{TPS{T,D}}}`    – `TPS` or `TPS` map to evaluate
  * `x::Union{Number,AbstractArray{<:Number}}` – Value(s) of the variable(s) to evaluate `m` at

`Evaluate` can also be called by "calling" `m`, e.g. `m(x)`, `m([x[1], x[2], ...])`, or  `m(x[1], x[2], ...)` is also allowed.
