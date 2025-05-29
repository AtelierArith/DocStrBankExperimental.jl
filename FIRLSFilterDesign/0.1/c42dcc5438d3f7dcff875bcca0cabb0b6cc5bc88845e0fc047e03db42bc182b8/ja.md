```
firls_design(filter_order::Integer, knotpoints_DW::Vector, D::Vector, W::Vector, antisymmetric::Bool; fs::Real = 1, solver::Function = \)
```

# 引数

  * `filter_order::Integer`   : FIRフィルタの次数。
  * `knotpoints_DW::Vector`   : 周波数のノットポイントを含むサイズ `(N,)` のベクトルで、[0, fs/2] をカバーします。
  * `D::Vector`               : `knotpoints_DW` の周波数ノットポイントに対する振幅応答値を含むサイズ `(N,)` のベクトル。
  * `W::Vector`               : `knotpoints_DW` の周波数ノットポイントに対する重み付け関数の値を含むサイズ `(N,)` のベクトル。
  * `antisymmetric::Bool`     : フィルタ係数が反対称であるかどうかを示すブール値。タイプ III および IV FIR フィルタで使用されます。
  * `fs::Real`                : サンプリング周波数。
  * `solver::Function`        : 方程式 $Qa = b$ を解くために呼び出される関数で、関数呼び出しは `solver(Q,b)` であり、`a` を返します。

# 出力

  * `h` : 線形位相 FIR フィルタ係数のベクトル。
