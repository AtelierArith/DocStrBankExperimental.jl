```
firls_design(filter_order::Integer, bands_DW::Matrix, D::Union{Vector,Matrix}, W::Union{Vector,Matrix}, antisymmetric::Bool; fs::Real = 1, solver::Function = \)
```

# 引数

  * `filter_order::Integer`   : FIRフィルタの次数。
  * `bands_DW::Matrix`        : サイズが `(N,2)` の行列で、[0, fs/2] の範囲にわたる連続した周波数バンドの行を含む。
  * `D::Union{Vector,Matrix}` : サイズが `(N,2)` の行列、またはサイズが `(N,)` のベクトルで、`bands_DW` の周波数バンドに対する振幅応答。行列の場合、最初と二番目の列は周波数バンドの下限と上限での振幅応答を示し、その間は線形補間される。ベクトルの場合、振幅応答は区分定数である。
  * `W::Union{Vector,Matrix}` : サイズが `(N,2)` の行列、またはサイズが `(N,)` のベクトルで、`bands_DW` の周波数バンドに対する重み付け関数の値を含む。行列の場合、最初と二番目の列は周波数バンドの下限と上限での重み付け関数の値を示し、その間は線形補間される。ベクトルの場合、重み付け関数は区分定数である。
  * `antisymmetric::Bool`     : フィルタ係数が反対称であるかどうかを示すブール値。これはタイプIIIおよびIVのFIRフィルタで使用される。
  * `fs::Real`                : サンプリング周波数。
  * `solver::Function`        : 方程式 $Qa = b$ を解くために呼び出される関数で、関数呼び出しは `solver(Q,b)` であり、`a` を返す。

# 出力

  * `h` : 線形位相FIRフィルタ係数のベクトル。
