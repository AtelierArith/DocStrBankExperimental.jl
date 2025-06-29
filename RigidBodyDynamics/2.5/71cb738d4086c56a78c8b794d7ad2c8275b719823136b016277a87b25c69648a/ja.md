```julia
mass_matrix!(M, state)

```

与えられた状態における `Mechanism` のジョイント空間質量行列（慣性行列とも呼ばれる）を計算します。すなわち、無制約ジョイント空間運動方程式における行列 $M(q)$ です。

$$
M(q) \dot{v} + c(q, v, w_\text{ext}) = \tau
$$

このメソッドは合成剛体アルゴリズムを実装しています。

このメソッドはインプレースで計算を行い、動的メモリ割り当ては行いません。

`out` 引数は $n_v \times n_v$ の下三角 `Symmetric` 行列でなければならず、ここで $n_v$ は `Mechanism` のジョイント速度ベクトル $v$ の次元です。
