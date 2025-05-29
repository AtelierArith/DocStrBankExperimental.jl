```
Integrate1D(F::Function, Cube::HyperCube; tol::Real=1e-14, FullSol::Bool=false, meth=Tsit5())
```

Integrates `F` over a one-dimensional domain specified via a `HyperCube` by rephrasing the integral as an ODE and using `DifferentialEquations.jl`.
