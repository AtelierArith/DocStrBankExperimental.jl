```
with_workspace(f,P)
```

In some cases, defining a primitive function which particles are to be propagate through is not possible but allowing unsafe comparisons are not acceptable. One such case is functions that internally calculate eigenvalues of uncertain matrices. The eigenvalue calculation makes use of comparison operators. If the uncertainty is large, eigenvalues might change place in the sorted list of returned eigenvalues, completely ruining downstream computations. For this we recommend, in order of preference

1. Use `@bymap` detailed [in the documentation](https://github.com/baggepinnen/MonteCarloMeasurements.jl#monte-carlo-simulation-by-mappmap). Applicable if all uncertain values appears as arguments to your entry function.
2. Create a `Workspace` object and call it using your entry function. Applicable if uncertain parameters appear nested in an object that is an argument to your entry function:

```julia
# desired computation: y = f(obj), obj contains uncertain parameters inside
y = with_workspace(f, obj)
# or equivalently
w = Workspace(f, obj)
use_invokelatest = true # Set this to false to gain 0.1-1 ms, at the expense of world-age problems if w is created and used in the same function.
w(obj, use_invokelatest)
```
