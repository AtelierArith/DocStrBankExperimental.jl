```
lin_fun, simplified_sys = linearization_function(sys::AbstractSystem, inputs, outputs; simplify = false, initialize = true, initialization_solver_alg = TrustRegion(), kwargs...)
```

Return a function that linearizes the system `sys`. The function [`linearize`](@ref) provides a higher-level and easier to use interface.

`lin_fun` is a function `(variables, p, t) -> (; f_x, f_z, g_x, g_z, f_u, g_u, h_x, h_z, h_u)`, i.e., it returns a NamedTuple with the Jacobians of `f,g,h` for the nonlinear `sys` (technically for `simplified_sys`) on the form

$$
\begin{aligned}
ẋ &= f(x, z, u) \\
0 &= g(x, z, u) \\
y &= h(x, z, u)
\end{aligned}
$$

where `x` are differential unknown variables, `z` algebraic variables, `u` inputs and `y` outputs. To obtain a linear statespace representation, see [`linearize`](@ref). The input argument `variables` is a vector defining the operating point, corresponding to `unknowns(simplified_sys)` and `p` is a vector corresponding to the parameters of `simplified_sys`. Note: all variables in `inputs` have been converted to parameters in `simplified_sys`.

The `simplified_sys` has undergone [`structural_simplify`](@ref) and had any occurring input or output variables replaced with the variables provided in arguments `inputs` and `outputs`. The unknowns of this system also indicate the order of the unknowns that holds for the linearized matrices.

# Arguments:

  * `sys`: An [`ODESystem`](@ref). This function will automatically apply simplification passes on `sys` and return the resulting `simplified_sys`.
  * `inputs`: A vector of variables that indicate the inputs of the linearized input-output model.
  * `outputs`: A vector of variables that indicate the outputs of the linearized input-output model.
  * `simplify`: Apply simplification in tearing.
  * `initialize`: If true, a check is performed to ensure that the operating point is consistent (satisfies algebraic equations). If the op is not consistent, initialization is performed.
  * `initialization_solver_alg`: A NonlinearSolve algorithm to use for solving for a feasible set of state and algebraic variables that satisfies the specified operating point.
  * `autodiff`: An `ADType` supported by DifferentiationInterface.jl to use for calculating the necessary jacobians. Defaults to using `AutoForwardDiff()`
  * `kwargs`: Are passed on to `find_solvables!`

See also [`linearize`](@ref) which provides a higher-level interface.
