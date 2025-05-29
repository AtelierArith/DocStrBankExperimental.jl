```
const VarξInput{T} = Union{ UniformScaling{T}, AbstractArray{T} }
```

Type used to characterize the assumption under which the weight matrix for the product level moments component of the objective function should be computed.  This is irrelevant for consistency, conformance, or the convergence rate of the estimator but it can affect asymptotic efficiency.
