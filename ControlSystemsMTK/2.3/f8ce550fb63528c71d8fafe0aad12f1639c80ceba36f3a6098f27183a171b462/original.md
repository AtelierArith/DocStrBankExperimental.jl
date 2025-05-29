```
ModelingToolkit.ODESystem(sys::AbstractStateSpace; name::Symbol, x0 = zeros(sys.nx), x_names, u_names, y_names)
```

Create an ODESystem from `sys::StateSpace`. 

# Arguments:

  * `sys`: An instance of `StateSpace` or `NamedStateSpace`.
  * `name`: A symbol giving the system a unique name.
  * `x0`: Initial state

The arguments below are automatically set if the system is a `NamedStateSpace`.

  * `x_names`: A vector of symbols with state names.
  * `u_names`: A vector of symbols with input names.
  * `y_names`: A vector of symbols with output names.
