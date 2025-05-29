```julia
inverse_dynamics(state, v̇)
inverse_dynamics(state, v̇, externalwrenches)

```

逆動力学を行います。すなわち、制約のない関節空間の運動方程式における $\tau$ を計算します。

$$
M(q) \dot{v} + c(q, v, w_\text{ext}) = \tau
$$

関節構成ベクトル $q$、関節速度ベクトル $v$、関節加速度ベクトル $\dot{v}$ および（オプションで）外部の力 $w_\text{ext}$ が与えられたときに計算します。

`externalwrenches` 引数は、`Mechanism` のボディに作用する追加の力を指定するために使用できます。

このメソッドは再帰的ニュートン-オイラーアルゴリズムを実装しています。

現在、サイクルを持つ `Mechanism` はサポートしていません。
