```julia
ode_order_lowering(sys::ModelingToolkit.ODESystem) -> Any

```

Takes a Nth order ODESystem and returns a new ODESystem written in first order form by defining new variables which represent the N-1 derivatives.
