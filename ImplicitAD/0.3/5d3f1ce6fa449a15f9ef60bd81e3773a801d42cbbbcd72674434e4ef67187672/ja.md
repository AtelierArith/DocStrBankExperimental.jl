```
implicit(solve, residual, x, p=(); drdy=drdy_forward, lsolve=linear_solve)
```

暗黙の関数をAD互換にする（特にForwardDiffおよびReverseDiffとの互換性）。

# 引数

  * `solve::function`: y = solve(x, p)。入力変数xと固定パラメータpに対して状態変数yを返す暗黙の関数を解く。
  * `residual::function`: r = residual(y, x, p)またはin-place residual!(r, y, x, p)。状態y（スカラーまたはベクトル）、変数x（ベクトル）、および固定パラメータp（タプル）に基づいて残差r（スカラーまたはベクトル）を設定します。
  * `x::vector{float}`: 評価点。
  * `p::tuple`: 固定パラメータ。デフォルトは空のタプルです。
  * `drdy::function`: drdy(residual, y, x, p)。∂r*i/∂y*jを提供（または自分で計算）します。デフォルトは前方モードADです。
  * `lsolve::function`: lsolve(A, b)。線形方程式A x = bを解く（ここでAはdrdyで計算され、bはjvpで計算されるか、A^T x = cを解く場合、cはvjpで計算されます）。デフォルトはバックスラッシュ演算子です。
