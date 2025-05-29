```
implicit_unsteady(initialize, onestep, residual, t, xd, xc, p=(); cache=nothing, drdy=drdy_forward, lsolve=linear_solve)
```

暗黙の非定常モードを逆モード効率的にする（ADと互換性のあるソルバー）。

# 引数:

  * `initialize::function`: 初期状態変数を返します。 `y0 = initialize(t0, xd, xc0, p)`。 t0（初期時間）、xd（設計変数）、xc0（初期制御変数）、p（固定パラメータ）に依存する場合としない場合があります。
  * `onestep::function`: 状態がどのように更新されるかを定義します（1ステップ法を仮定）。 `y = onestep(yprev, t, tprev, xd, xci, p)` またはインプレース `onestep!(y, yprev, t, tprev, xd, xci, p)`。 前の状態 `yprev`、現在の時間 `t`、前の時間 `tprev`、設計変数 `xd`、その時間ステップの現在の制御変数 `xci`、および固定パラメータ `p` に基づいて次の状態変数 `y` を設定します。
  * `residual::function`: onestepで解決される残差を定義します。 変数は上記と同じである `r = residual(y, yprev, t, tprev, xd, xci, p)` または `residual!(r, y, yprev, t, tprev, xd, xci, p)`。
  * `t::vector{float}`: シミュレーションが実行される時間ステップ
  * `xd::vector{float}`: 設計変数、時間に依存せず、実行ごとに変化します（そうでなければパラメータになります）
  * `xc::matrix{float}`, サイズ nxc x nt: 制御変数。 xc[:, i] は i 番目の時間ステップでの制御変数です。
  * `p::tuple`: 固定パラメータ、すなわち常に一定であり、したがって導関数に影響を与えません。 デフォルトは空のタプルです。

# キーワード引数:

  * `cache=nothing`: `implicit_unsteady_cache` を参照してください。 1回以上導関数を計算する場合は、事前にキャッシュを計算して後の反復のために保存する必要があります。 そうでなければ、内部で作成されます。
  * `drdy`: drdy(residual, r, y, yprev, t, tprev, xd, xci, p)。 提供する（または自分で計算する）：∂ri/∂yj。 デフォルトは前方モードADです。
  * `lsolve::function`: `lsolve(A, b)`。 線形解法 `A x = b`（ここで `A` は `drdy` で計算され、`b` は `jvp` で計算されるか、`A^T x = c` を解く場合、`c` は `vjp` で計算されます）。 デフォルトはバックスラッシュ演算子です。
