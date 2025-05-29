```julia
configuration_derivative_to_velocity_adjoint!(
    fq,
    joint,
    q,
    fv
)

```

線形関数が与えられたとき

$$
f(v) = \langle f_v, v \rangle
$$

ここで $v$ は関節の速度ベクトルであり、ベクトル $f_q$ を返すことが求められます。これは次のように表されます。

$$
\langle f_v, v \rangle = \langle f_q, \dot{q}(v) \rangle.
$$

注意: $v$ は $\dot{q}$ の線形関数であるため（[`configuration_derivative_to_velocity!`](@ref)を参照）、$v = J_{\dot{q} \rightarrow v} \dot{q}$ と書くことができます。したがって、

$$
\langle f_v, v \rangle = \langle f_v, J_{\dot{q} \rightarrow v} \dot{q} \rangle = \langle J_{\dot{q} \rightarrow v}^{*} f_v, \dot{q} \rangle
$$

したがって $f_q = J_{\dot{q} \rightarrow v}^{*} f_v$ です。

$$
J_{\dot{q} \rightarrow v}
$$

を計算するには、[`configuration_derivative_to_velocity_jacobian`](@ref)を参照してください。
