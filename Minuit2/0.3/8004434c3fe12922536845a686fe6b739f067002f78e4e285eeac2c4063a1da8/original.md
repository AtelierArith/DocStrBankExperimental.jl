```
FCN(cost::CostFunction, grad=true)
```

Create a JuliaFcn object from a CostFunction.

## Arguments

  * `fnc::CostFunction` : The CostFunction to minimize.
  * `grad::Bool=true` : If `true`, the gradient of the cost function is used. If `false`, the gradient is not used.

## Returns

  * `JuliaFcn` : A JuliaFcn object inheriting from the abstract C++ class `Minuit::FCNBase`that can be used in Minuit.
