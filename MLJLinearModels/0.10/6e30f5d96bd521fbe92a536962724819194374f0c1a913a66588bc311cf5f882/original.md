```julia
struct LPPenalty{p} <: MLJLinearModels.AtomicPenalty
```

Scaled L-p norm of the parameter vector.

$P(θ) = ||θ||_{p}^{p}/p$

The scaling simplifies expressions in the common L2 case.
