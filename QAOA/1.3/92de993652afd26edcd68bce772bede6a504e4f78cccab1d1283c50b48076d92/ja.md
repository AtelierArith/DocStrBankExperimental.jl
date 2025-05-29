```
cost_function(problem::Problem, beta_and_gamma::Vector{Float64})
```

QAOAコスト関数、すなわち問題ハミルトニアンの期待値を返します。

### 入力

  * `problem::Problem`: 最適化問題を定義する`Problem`インスタンス。
  * `beta_and_gamma::Vector{Float64}`: QAOAパラメータのベクトル。

### 出力

  * 問題ハミルトニアンの期待値。

### 注意事項

この関数は次を計算します。

$$
\langle \hat H \rangle = \left\langle \sum_{i=1}^N\left( h_i \hat Z_i + \sum_{j>i} J_{ij}\hat Z_i \hat Z_j \right)\right\rangle,
$$

ここで、$N$は`num_qubits`、$h_i$は`local_fields`、$J_{ij}$は`problem`からの`couplings`です。
