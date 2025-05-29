```julia
dynamics_bias(state)
dynamics_bias(state, externalwrenches)

```

'dynamics bias term'を計算します。すなわち、次の項

$$
c(q, v, w_\text{ext})
$$

を無拘束関節空間の運動方程式において

$$
M(q) \dot{v} + c(q, v, w_\text{ext}) = \tau
$$

与えられた関節構成ベクトル$q$、関節速度ベクトル$v$、関節加速度ベクトル$\dot{v}$、および（オプションで）外部の力$w_\text{ext}$。

`externalwrenches`引数は、`Mechanism`のボディに作用する追加の力を指定するために使用できます。
