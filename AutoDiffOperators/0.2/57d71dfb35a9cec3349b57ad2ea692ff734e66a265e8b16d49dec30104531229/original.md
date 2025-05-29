```
DiffIfAD{Fwd<:ADSelector,Rev<:ADSelector} <: ADSelector
```

Uses [DifferentiationInterfac](https://github.com/gdalle/DifferentiationInterface.jl) to interface with an AD-backend.

Constructor: `DiffIfAD(backend::ADTypes.AbstractADType)`
