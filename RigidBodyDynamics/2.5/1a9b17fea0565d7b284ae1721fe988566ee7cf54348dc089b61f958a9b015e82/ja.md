```julia
inverse_dynamics!(
    torquesout,
    jointwrenchesout,
    accelerations,
    state,
    v̇
)
inverse_dynamics!(
    torquesout,
    jointwrenchesout,
    accelerations,
    state,
    v̇,
    externalwrenches
)

```

逆動力学を行います。すなわち、制約のない関節空間の運動方程式における $\tau$ を計算します。

$$
M(q) \dot{v} + c(q, v, w_\text{ext}) = \tau
$$

関節構成ベクトル $q$、関節速度ベクトル $v$、関節加速度ベクトル $\dot{v}$、および（オプションで）外部トルク $w_\text{ext}$ が与えられます。

`externalwrenches` 引数は、`Mechanism` のボディに作用する追加のトルクを指定するために使用できます。

このメソッドは、再帰的ニュートン-オイラーアルゴリズムを実装しています。

現在、サイクルを持つ `Mechanism` はサポートしていません。

このメソッドは、動的メモリ割り当てを行わずにインプレースで計算を行います。
