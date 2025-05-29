```julia
struct LogisticLoss <: MLJLinearModels.AtomicLoss
```

$L(x, y) = -∑logσ(xᵢyᵢ)$

where `logσ` is the log of the sigmoid function; `yᵢ ∈ {±1}`. In a logistic regression `x` corresponds to `Xθ` where `X` is the design matrix and `θ` the vector of parameters. See [`logsigmoid`](@ref).
