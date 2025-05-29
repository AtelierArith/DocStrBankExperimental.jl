```
explicit_unsteady(initialize, onestep, solve, t, xd, xc, p=(); cache=nothing)
```

明示的なODEに対して逆モードを効率的にします。各時間ステップごとにテープを別々に構築し、全体の時間シーケンスにわたって長いテープを記録するのではなく、間で解析的に伝播させます。

# 引数:

  * `initialize::function`: 初期状態変数を返します。 `y0 = initialize(t0, xd, xc0, p)`。 t0（初期時間）、xd（設計変数）、xc0（初期制御変数）、p（固定パラメータ）に依存する場合としない場合があります。
  * `onestep::function`: 状態がどのように更新されるかを定義します（1ステップ法を仮定）。 `y = onestep(yprev, t, tprev, xd, xci, p)` またはインプレース `onestep!(y, yprev, t, tprev, xd, xci, p)`。 前の状態 `yprev`、現在の時間 `t`、前の時間 `tprev`、設計変数 `xd`、現在の制御変数 `xc`、および固定パラメータ `p` に基づいて次の状態変数 `y` を設定します。
  * `t::vector{float}`: シミュレーションが実行される時間ステップ
  * `xd::vector{float}`: 設計変数、時間に依存せず、1回の実行から次の実行に変化します（そうでなければパラメータになります）。
  * `xc::matrix{float}`, サイズ nxc x nt: 制御変数。 xc[:, i] は i 番目の時間ステップでの制御変数です。
  * `p::tuple`: 固定パラメータ、すなわち常に一定であり、したがって導関数に影響を与えません。 デフォルトは空のタプルです。

# キーワード引数:

  * `cache=nothing`: `explicit_unsteady_cache` を参照してください。 もし導関数を複数回計算する場合は、事前にキャッシュを計算して後の反復のために保存するべきです。 そうでなければ、内部で作成されます。
