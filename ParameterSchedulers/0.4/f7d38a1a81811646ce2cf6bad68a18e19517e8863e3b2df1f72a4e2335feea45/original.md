```
Step{T, S<:Integer}(start, decay, step_sizes)
Step(; start, decay, step_sizes)
```

A step schedule decays exponentially by `decay` every step in `step_sizes`. The output conforms to

```text
start * decay^{i - 1}
```

where `sum(step_sizes[1:(i - 1)]) < t <= sum(step_sizes[1:i])`

# Arguments

  * `start`: the starting value
  * `decay`: the decay rate
  * `step_sizes::Union{<:Integer, <:Vector}`: the step sizes
