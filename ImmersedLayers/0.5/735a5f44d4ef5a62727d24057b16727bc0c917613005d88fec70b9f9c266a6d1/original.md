The `@ilmproblem` macro is used to automatically generate a type particular to an immersed-layer problem, which can then be used for dispatch on those types of problems. It takes two arguments: the name of the problem (to which `Problem` will be automatically appended), and whether the problem is of scalar or vector type. For example,

```
@ilmproblem(StokesFlow,vector)
```

would generate a type `StokesFlowProblem` dealing with vector-valued data. The resulting type then automatically has a constructor that allows one to pass in the grid information and bodies, as well as optional choices for the DDF function and the scaling type. For the example, this constructor would be

```
StokesFlowProblem(grid,bodies[,ddftype=CartesianGrids.Yang3][,scaling=GridScaling])
```

Note that there is another constructor for problems with no surfaces that only requires that the grid information be passed, e.g.,

```
StokesFlowProblem(grid)
```

There are several keyword arguments for the problem constructor

  * `ddftype =` to set the DDF type. The default is `Yang3`.
  * `scaling =` to set the scaling type, `GridScaling` (default) or `IndexScaling`.
  * `dtype =` to set the element type to `Float64` (default) or `ComplexF64`.
  * `phys_params =` to pass in physical parameters
  * `bc =` to pass in boundary condition data or functions
  * `forcing =` to pass in forcing functions or data
  * `motions =` to provide function(s) that specify the velocity of the immersed surface(s). Note: if this keyword is used, it is assumed that surfaces will move.
  * `reference_body =` to provide the ID of the body whose axes the problem is solved in
  * `timestep_func =` to pass in a function for time-dependent problems that provides the time-step size.                 It is expected that this function takes in two arguments,                 the `grid::PhysicalGrid` and `phys_params`, and returns the time step. It is up to the                 user to decide how to determine this. It could also simply return a                 constant value, regardless of the arguments.
