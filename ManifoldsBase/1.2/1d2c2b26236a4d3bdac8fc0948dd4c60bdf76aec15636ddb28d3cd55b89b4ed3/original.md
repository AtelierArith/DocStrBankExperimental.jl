```
NLSolveInverseRetraction{T<:AbstractRetractionMethod,TV,TK} <:
    ApproximateInverseRetraction
```

An inverse retraction method for approximating the inverse of a retraction using `NLsolve`.

# Constructor

```
NLSolveInverseRetraction(
    method::AbstractRetractionMethod[, X0];
    project_tangent=false,
    project_point=false,
    nlsolve_kwargs...,
)
```

Constructs an approximate inverse retraction for the retraction `method` with initial guess `X0`, defaulting to the zero vector. If `project_tangent` is `true`, then the tangent vector is projected before the retraction using `project`. If `project_point` is `true`, then the resulting point is projected after the retraction. `nlsolve_kwargs` are keyword arguments passed to `NLsolve.nlsolve`.
