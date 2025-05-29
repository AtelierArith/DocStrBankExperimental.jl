```julia
struct LPLoss{p} <: MLJLinearModels.AtomicLoss
```

Scaled L-p loss of the residual.

$L(x, y) = ||x-y||_{p}^{p}/p$

The scaling simplifies expressions in the common L2 case.
