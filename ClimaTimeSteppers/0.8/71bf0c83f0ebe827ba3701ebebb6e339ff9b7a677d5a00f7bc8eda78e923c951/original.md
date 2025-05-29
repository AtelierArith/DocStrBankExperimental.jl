```
ARK2GKC(; paper_version = false)
```

An IMEX ARK algorithm from [GKC2013](@cite) with 2 implicit stages, 3 explicit stages, and 2nd order accuracy. If `paper_version = true`, the algorithm uses coefficients from the paper. Otherwise, it uses coefficients that make it more stable but less accurate.
