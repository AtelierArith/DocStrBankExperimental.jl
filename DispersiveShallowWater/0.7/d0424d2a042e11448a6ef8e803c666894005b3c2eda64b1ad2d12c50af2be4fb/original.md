```
prim2phys(q, equations)
```

Convert the primitive variables `q` to the physically meaningful variables for a given set of `equations`. By default, this is the same as [`prim2prim`](@ref) for most equations. However, some equations like the [`HyperbolicSerreGreenNaghdiEquations1D`](@ref) return a reduced set of variables since they are a hyperbolic approximation of another set of equations (in this case the [`SerreGreenNaghdiEquations1D`](@ref)).

See also [`is_hyperbolic_appproximation`](@ref) and [`hyperbolic_approximation_limit`](@ref).

`q` is a vector type of the correct length `nvariables(equations)`. Notice the function doesn't include any error checks for the purpose of efficiency, so please make sure your input is correct.
