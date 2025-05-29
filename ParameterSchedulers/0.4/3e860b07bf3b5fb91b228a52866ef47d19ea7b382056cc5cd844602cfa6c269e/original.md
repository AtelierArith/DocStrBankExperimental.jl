```
Exp{T}(start, decay)
Exp(; start, decay)
```

A exponential decay schedule at rate `decay`. The output conforms to

```text
start * decay^{t - 1}
```

# Arguments:

  * `start`: the base value
  * `decay`: the decay rate
