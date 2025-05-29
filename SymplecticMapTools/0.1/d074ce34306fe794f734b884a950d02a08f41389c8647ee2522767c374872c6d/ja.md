```
newton_periodic(FJ::Function, x::AbstractVector, q::Integer;
                maxiter::Integer=50, rtol::Number=1e-8, verbose::Bool=false)
```

ニュートン法を用いて線形探索で周期軌道を見つける

引数:

  * `FJ`: マップとその導関数 `F, dFdx = FJ(x)` を返す関数
  * `x`: 軌道を見つけるための初期点
  * `q`: 軌道の周期
  * `maxiter=50`: 許可される最適化ステップの最大数
  * `rtol=1e-8`: 必要な残差許容値
  * `verbose=false`: true の場合、収束に関する情報を出力

出力:

  * `xs`: 長さ `d` の周期的軌道
  * `converged`: 軌道が `maxiter` ステップで収束したかどうかを示すフラグ
