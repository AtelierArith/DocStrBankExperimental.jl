```julia
dynamics!(ẋ, result, state, x; ...)
dynamics!(ẋ, result, state, x, torques; ...)
dynamics!(
    ẋ,
    result,
    state,
    x,
    torques,
    externalwrenches;
    stabilization_gains
)

```

Convenience function for use with standard ODE integrators that takes a `Vector` argument

$$
x = \left(\begin{array}{c}
q\\
v
\end{array}\right)
$$

and returns a `Vector` $\dot{x}$.
