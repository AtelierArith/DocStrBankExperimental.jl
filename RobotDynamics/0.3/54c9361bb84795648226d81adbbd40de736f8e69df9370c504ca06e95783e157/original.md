```
∇f = jacobian!(∇f, model, z::AbstractKnotPoint)
```

Compute the `n × (n + m)` Jacobian `∇f` of the continuous-time dynamics using ForwardDiff. Only accepts an `AbstractKnotPoint` as input in order to avoid potential allocations associated with concatenation.
