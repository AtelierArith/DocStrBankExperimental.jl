```
update!(
    P::Predictor,
    H::AbstractHomotopy,
    x,
    t,
    jacobian::Jacobian,
    norm::AbstractNorm,
    x̂ = nothing,
)
```

Upadte the predictor with the new solution `(x,t)` of `H(x,t) = 0`. This computes new local derivatives and chooses an appriopriate prediction method.
