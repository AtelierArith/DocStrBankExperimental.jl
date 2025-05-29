```
Convexification
```

Factory object for using convexification to handle integer recourse. Pass to `integer_strategy` in `LShaped.Optimizer` or set the [`IntegerStrategy`](@ref) attribute.

...

# Parameters

  * `maximum_iterations::Integer = 1`: Determines the number of iterations spent generating cutting-planes each time a subproblem is solved.
  * `strategy::ConvexificationStrategy = Gomory()`: Specify convexification strategy (`Gomory`, `LiftAndProject`, `CuttingPlaneTree`)
  * `optimizer = nothing`: Optionally specify an optimizer used to solve auxilliary problems in the `LiftAndProject` or `CuttingPlaneTree` strategies.

...
