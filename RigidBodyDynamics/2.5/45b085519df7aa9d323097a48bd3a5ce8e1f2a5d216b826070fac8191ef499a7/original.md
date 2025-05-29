```julia
configuration_derivative_to_velocity_adjoint!(
    fq,
    joint,
    q,
    fv
)

```

Given  a linear function

$$
f(v) = \langle f_v, v \rangle
$$

where $v$ is the joint velocity vector, return a vector $f_q$ such that

$$
\langle f_v, v \rangle = \langle f_q, \dot{q}(v) \rangle.
$$

Note: since $v$ is a linear function of $\dot{q}$ (see [`configuration_derivative_to_velocity!`](@ref)), we can write $v = J_{\dot{q} \rightarrow v} \dot{q}$, so

$$
\langle f_v, v \rangle = \langle f_v, J_{\dot{q} \rightarrow v} \dot{q} \rangle = \langle J_{\dot{q} \rightarrow v}^{*} f_v, \dot{q} \rangle
$$

so $f_q = J_{\dot{q} \rightarrow v}^{*} f_v$.

To compute $J_{\dot{q} \rightarrow v}$ see [`configuration_derivative_to_velocity_jacobian`](@ref).
