```
ORBIT{N, VT, AM} <: AbstractContinuousPost
```

Implementation of discrete-time integration for deterministic linear ODEs for singleton initial conditions and proper input sets.

## Fields

  * `δ`            – step-size of the discretization
  * `approx_model` – (optional, default: `NoBloating`) approximation model

The type fields are:

  * `N`  – number type of the step-size
  * `AM` – type of the approximation model

## Notes

If the input set is a singleton, the result is the discrete-time sequence of states that correspond to the analytic solution. If the input set is a dense set, we sample a new input signal in every step.

Reachability solutions computed with the `ORBIT` algorithm have its own plot recipe, producing a scatter plot. Use the `markershape` option to change the shape of the markers used for the scatter plot. To "connect" the points, use the option `seriestype=:path`. For additional options see the [Plots.jl documentation](https://docs.juliaplots.org/latest/generated/attributes_series/).
