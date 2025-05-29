```
firls_design(filter_order::Integer, knotpoints_D::Vector, D::Vector, antisymmetric::Bool; fs::Real = 1, solver::Function = \)
```

# 引数

  * `filter_order::Integer`   : FIRフィルタの次数。
  * `knotpoints_D::Vector`    : サイズが `(N,)` のベクトルで、周波数のノットポイントを含み、範囲は [0, fs/2]。
  * `D::Vector`               : サイズが `(N,)` のベクトルで、`knotpoints_D::Vector` の周波数ノットポイントに対する振幅応答値を含む。
  * `antisymmetric::Bool`     : フィルタ係数が反対称であるかどうかを示すブール値。これはタイプ III および IV FIR フィルタで使用される。
  * `fs::Real`                : サンプリング周波数。
  * `solver::Function`        : 方程式 $Qa = b$ を解くために呼び出される関数。関数呼び出しは `solver(Q,b)` で、`a` を返す。

# 出力

  * `h` : 線形位相FIRフィルタ係数のベクトル。
