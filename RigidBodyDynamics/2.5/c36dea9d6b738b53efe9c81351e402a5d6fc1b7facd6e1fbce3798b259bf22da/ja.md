```julia
dynamics_bias!(torques, biasaccelerations, wrenches, state)
dynamics_bias!(
    torques,
    biasaccelerations,
    wrenches,
    state,
    externalwrenches
)

```

「ダイナミクスバイアステーム」、すなわち

$$
c(q, v, w_\text{ext})
$$

を無拘束関節空間の運動方程式で計算します。

$$
M(q) \dot{v} + c(q, v, w_\text{ext}) = \tau
$$

関節構成ベクトル $q$、関節速度ベクトル $v$、関節加速度ベクトル $\dot{v}$、および（オプションで）外部トルク $w_\text{ext}$ が与えられます。

`externalwrenches` 引数は、`Mechanism` のボディに作用する追加のトルクを指定するために使用できます。

このメソッドは、動的メモリ割り当てを行わずにインプレースで計算を行います。
