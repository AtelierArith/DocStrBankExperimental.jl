```
implicit_unsteady_cache(initialize, residual, ny, nxd, nxc, p=(); compile=false)
```

暗黙の非定常逆モードに必要な配列と関数を初期化します

# 引数

  * `initialize::function`: 初期状態変数を返します。 `y0 = initialize(t0, xd, xc0, p)`。 t0（初期時間）、xd（設計変数）、xc0（初期制御変数）、p（固定パラメータ）に依存する場合としない場合があります。
  * `residual::function`: onestepで解決される残差を定義します。 変数は上記と同じである `r = residual(y, yprev, t, tprev, xd, xci, p)` または `residual!(r, y, yprev, t, tprev, xd, xci, p)` のいずれかです。
  * `ny::int`: 状態の数
  * `nxd::int`: 設計変数の数
  * `nxc::int`: 制御変数の数（特定の時間ステップで）
  * `p::tuple`: 固定パラメータ、すなわち常に一定であり、したがって導関数に影響を与えません。 デフォルトは空のタプルです。
  * `compile::bool`: `onestep`関数のテープを事前に記録できるかどうかを示します。 はるかに速くなりますが、`onestep`に分岐が含まれていない場合にのみ`true`にすべきです。 そうでない場合、ReverseDiffは不正確な勾配を返す可能性があります。
