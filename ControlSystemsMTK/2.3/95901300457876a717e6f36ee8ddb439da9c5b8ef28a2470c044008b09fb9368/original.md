```
linsystems, ssys = trajectory_ss(sys, inputs, outputs, sol; t = _max_100(sol.t), fuzzer=nothing, verbose = true, kwargs...)
```

Linearize `sys` around the trajectory `sol` at times `t`. Returns a vector of `StateSpace` objects and the simplified system.

# Arguments:

  * `inputs`: A vector of variables or analysis points.
  * `outputs`: A vector of variables or analysis points.
  * `sol`: An ODE solution object. This solution must contain the states of the simplified system, accessible through the `idxs` argument like `sol(t, idxs=x)`.
  * `t`: Time points along the solution trajectory at which to linearize. The returned array of `StateSpace` objects will be of the same length as `t`.
  * `fuzzer`: A function that takes an operating point dictionary and returns an array of "fuzzed" operating points. This is useful for adding noise/uncertainty to the operating points along the trajectory. See [`ControlSystemsMTK.fuzz`](@ref) for such a function.
  * `verbose`: If `true`, print warnings for variables that are not found in `sol`.
  * `kwargs`: Are sent to the linearization functions.
