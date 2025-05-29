```julia
mutable struct Orbit{FR, F, MU, LU, TU, AU, E, S, P} <: GeneralAstrodynamics.States.AbstractOrbit{FR, F, MU, LU, TU, AU, E, S, P}
```

`StateVector`によって記述された軌道で、`ParameterVector`によって記述されたパラメータを持ちます。
