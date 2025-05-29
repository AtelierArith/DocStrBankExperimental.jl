```
firls_design(filter_order::Integer, bands_DW::Matrix, D::Matrix, W::Matrix, antisymmetric::Bool; fs::Real = 1, solver::Function = \)
```

線形位相FIRフィルタを設計します。

# 引数

  * `filter_order::Integer`   : FIRフィルタの次数。
  * `bands_DW::Matrix`        : [0, fs/2]を跨ぐ連続した周波数帯の行を含むサイズ(N,2)の行列。
  * `D::Matrix`               : `bands_DW`の周波数帯に対する振幅応答の行を含むサイズ(N,2)の行列。最初の列と2番目の列は、周波数帯の下限と上限での振幅応答を示し、その間は線形補間されます。
  * `W::Matrix`               : `bands_DW`の周波数帯に対する重み係数の行を含むサイズ(N,2)の行列。最初の列と2番目の列は、周波数帯の下限と上限での重みを示し、その間は線形補間されます。
  * `antisymmetric::Bool`     : フィルタ係数が反対称であるかどうかを示すブール値。これはタイプIIIおよびIVのFIRフィルタで使用されます。
  * `fs::Real`                : サンプリング周波数。
  * `solver::Function`        : 方程式$Qa = b$を解くために呼び出される関数で、関数呼び出しは`solver(Q,b)`であり、`a`を返します。

# 出力

  * `h` : 線形位相FIRフィルタ係数のベクトル。
