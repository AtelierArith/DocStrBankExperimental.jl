```
explicit_unsteady_cache(initialize, onestep!, ny, nxd, nxc, p=(); compile=false)
```

明示的非定常逆モードに必要な配列と関数を初期化します

# 引数

  * `initialize::function`: 初期状態変数を返します。 `y0 = initialize(t0, xd, xc0, p)`。 t0（初期時間）、xd（設計変数）、xc0（初期制御変数）、p（固定パラメータ）に依存する場合としない場合があります。
  * `onestep::function`: 状態がどのように更新されるかを定義します（1ステップ法を仮定）。 `y = onestep(yprev, t, tprev, xd, xci, p)` またはインプレース `onestep!(y, yprev, t, tprev, xd, xci, p)`。 前の状態 `yprev`、現在の時間 `t`、前の時間 `tprev`、設計変数 `xd`、その時間ステップの現在の制御変数 `xci`、および固定パラメータ `p` に基づいて次の状態変数 `y` を設定します。
  * `ny::int`: 状態の数
  * `nxd::int`: 設計変数の数
  * `nxc::int`: 制御変数の数（特定の時間ステップで）
  * `p::tuple`: 固定パラメータ、すなわち常に一定であり、したがって導関数に影響を与えません。 デフォルトは空のタプルです。
  * `compile::bool`: `onestep` 関数のテープが事前に記録できるかどうかを示します。 これははるかに速くなりますが、`onestep` に分岐が含まれていない場合にのみ `true` であるべきです。 そうでない場合、ReverseDiff は不正確な勾配を返す可能性があります。
