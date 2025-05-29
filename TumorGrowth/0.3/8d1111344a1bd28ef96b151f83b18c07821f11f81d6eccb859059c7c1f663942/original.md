```
bertalanffy_numerical(times, p; solve_kwargs...)
```

*Provided for testing purposes.*

Return volumes for specified `times`, based on numerical solutions to the General Bertalanffy model for lesion growth. Here `p` will have properties `v0`, `v∞`, `ω`, `λ`, where `v0` is the volume at time `times[1]`; `solve_kwargs` are optional keyword arguments for the ODE solver, `DifferentialEquations.solve`, from DifferentialEquations.jl.

Since it is based on analtic solutions, [`bertalanffy`](@ref) is the preferred alternative to this function.

!!! important
    It is assumed without checking that `times` is ordered: `times == sort(times)`.


See also [`bertalanffy2`](@ref).
