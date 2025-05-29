```
Inv{T, S<:Integer}(start, decay, degree)
Inv(; start, decay, degree)
```

A decay schedule that inversely decays with rate `decay`. The output conforms to

```text
start / (1 + (t - 1) * decay)^degree
```

# Arguments

  * `start`: the base value
  * `decay`: the decay rate
  * `degree::Integer`: the degree of decay
