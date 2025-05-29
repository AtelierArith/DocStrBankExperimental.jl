```
(ls::HagerZhangLineSearch)(fg, x₀, η₀, fg₀ = fg(x₀);
                retract = _retract, inner = _inner,
                initialguess = one(fg₀[1]), acceptfirst = false,
                maxiter = ls.maxiter, maxfg = lsmaxfg, verbosity = ls.verbosity)
```

Hager-Zhang線形探索を実行して、（近似的な）Wolfe条件を満たすステップ長を見つけます。

## 引数:

  * `ls::HagerZhangLineSearch`: HagerZhangLineSearchオブジェクト。
  * `fg`: 目的関数とその勾配を計算する関数。
  * `x₀`: 開始点。
  * `η₀`: 探索方向。
  * `fg₀`: `x₀`で評価された目的関数と勾配。デフォルトは`fg(x₀)`ですが、この情報がすでに計算されている場合は提供できます。

## キーワード引数:

  * `retract`: 縮小ステップを実行する関数、すなわち`x₀ + α * η₀`の一般化。デフォルトは`_retract`。
  * `inner`: 探索方向と勾配の内積を計算する関数。デフォルトは`_inner`。
  * `initialguess::Real`: ステップ長の初期推測。デフォルトは`one(fg₀[1])`。
  * `acceptfirst::Bool`: 初期推測が強いWolfe条件を満たす場合に受け入れられるかどうかを制御するパラメータ。デフォルトは`false`で、少なくとも1回の線形探索反復と1回の追加関数評価が必要です。
  * `maxiter::Int`: 反復回数のハードリミット。デフォルトは`50`。
  * `maxfg::Int`: 関数評価のソフトリミット。デフォルトは`100`。
  * `verbosity::Int`: 冗長性レベル（下記参照）。デフォルトは`0`。

### 冗長性レベル

  * `0`: 出力なし。
  * `1`: 線形探索が終了したときの収束に関する単一出力。
  * `2`: Hager-Zhang線形探索の開始後と各個別反復ステップ後の出力。
  * `3`: 初期ブランケットとさらなるブランケット更新および二分法ステップに関する追加出力。
  * `4`: ブランケット、更新、および二分法ステップでの各関数評価後の出力。

## 戻り値:

  * `x`: （近似的な）Wolfe条件が満たされる点`retract(x₀, η₀, α)`。
  * `f`: `x`での関数値。
  * `g`: `x`での勾配。
  * `ξ`: 線形探索パスに対する`x`での接線。
  * `α`: （近似的な）Wolfe条件を満たすステップ長。
  * `numfg`: 実行された関数評価の数。
