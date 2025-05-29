```
deim(
    sys::ModelingToolkit.ODESystem,
    snapshot::AbstractMatrix,
    pod_dim::Integer;
    deim_dim::Integer = pod_dim,
    name::Symbol = Symbol(nameof(sys), :_deim),
    kwargs...
) -> ModelingToolkit.ODESystem
```

Reduce a `ModelingToolkit.ODESystem` using the Proper Orthogonal Decomposition (POD) with the Discrete Empirical Interpolation Method (DEIM).

`snapshot` should be a matrix with the data of each time instance as a column.

The LHS of equations in `sys` are all assumed to be 1st order derivatives. Use `ModelingToolkit.ode_order_lowering` to transform higher order ODEs before applying DEIM.

`sys` is assumed to have no internal systems. End users are encouraged to call `ModelingToolkit.structural_simplify` beforehand.

The POD basis used for DEIM interpolation is obtained from the snapshot matrix of the nonlinear terms, which is computed by executing the runtime-generated function for nonlinear expressions.
