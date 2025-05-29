```
gn_circle(FJ::Function, z::InvariantCircle, Nθ::Integer;
          maxiter::Integer=10, rtol::Number=1e-8, verbose::Bool=false,
          monitor::Function=(z, rnorm) -> nothing,
          constraint::Function=fixed_θ0_constraint, λ::Number=0)
```

ガウス-ニュートン法を用いて不変円を見つけます。密な線形代数で実装されています（まだFFTは使用していません）。収束にかかった反復回数を返します。評価が失敗した場合は `-1` を返します。ルーチンが収束しなかった場合は `-2` を返します。

引数:

  * `z::InvariantCircle`: 初期接続軌道の推測、`linear_initial_connecting_orbit` を参照してください
  * `FJ::Function`: R²上で定義された関数で、シグネチャは `F(x), J(x) = FJ(x)` であり、`F` はシンプレクティック写像、`J = dF/dx` です
  * `Nθ`: 最小二乗法のための数値積分ノードの数
  * `maxiter = 10`: ガウス-ニュートンステップの最大数
  * `rtol = 1e-8`: 停止許容誤差
