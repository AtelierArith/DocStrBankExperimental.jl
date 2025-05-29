```
DiffEqBase.ODEProblem(sys::FSPSystem, u0, tmax[, p])
```

`DifferentialEquations`で使用するための`ODEProblem`を返します。この関数は暗黙的に`convert(ODEFunction, sys)`を呼び出します。通常、最初に`ODEFunction`を作成し、それを使用して`ODEProblem`を作成する方が効率的です。
