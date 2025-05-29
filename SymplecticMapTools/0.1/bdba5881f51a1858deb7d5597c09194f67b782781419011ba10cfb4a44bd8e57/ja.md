```
BFGS_periodic(FJ::Function, x::AbstractVector, q::Integer;
              maxiter::Integer=50)
```

BFGSを使用して周期軌道を見つけます（Optimパッケージから）。

引数:

  * `FJ`: マップとその導関数を返す関数 `F, dFdx = FJ(x)`
  * `x`: 軌道を見つけるための初期点
  * `q`: 軌道の周期
  * `maxiter=50`: 許可される最適化ステップの最大数

出力:

  * `xs`: 長さ `d` の周期的軌道
  * `res`: Optimの戻りオブジェクト（`Optim.converged(res)`で収束を確認できます）
