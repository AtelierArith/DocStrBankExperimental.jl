```
gn_connecting!(c::ConnectingOrbit, FJ::Function, ends::AbstractArray;
               Ns = 100, maxiters = 10, rtol = 1e-8, verbose=false)
```

ガウス・ニュートン法を用いて接続軌道を見つけます。

引数:

  * `c::ConnectingOrbit`: 初期接続軌道の推測、`linear_initial_connecting_orbit`を参照してください
  * `FJ::Function`: R²上で定義された関数で、シグネチャは `F(x), J(x) = FJ(x)` であり、`F` はシンプレクティック写像、`J = dF/dx` です
  * `ends::AbstractArray`: 終端周期軌道を含む 2p × 2 行列 `[x00, x10; F(x00), F(x10); ... ; F^(p-1)(x00), F^(p-1)(x10)]`
  * `Ns = 100`: 最小二乗法のための数値積分ノードの数
  * `maxiters = 10`: ガウス・ニュートン法の最大ステップ数
  * `rtol = 1e-8`: 停止許容誤差
