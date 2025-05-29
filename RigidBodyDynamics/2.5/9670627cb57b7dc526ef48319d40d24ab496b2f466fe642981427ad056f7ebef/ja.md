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

標準ODE積分器で使用するための便利な関数で、`Vector`引数を取ります。

$$
x = \left(\begin{array}{c}
q\\
v
\end{array}\right)
$$

および`Vector` $\dot{x}$を返します。
