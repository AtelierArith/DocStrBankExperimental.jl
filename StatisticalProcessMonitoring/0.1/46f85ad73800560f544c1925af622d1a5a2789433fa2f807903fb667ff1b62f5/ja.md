```
optimize_design!(CH::ControlChart, rlsim_oc::Function, settings::OptSettings=OptSettings(CH); optimizer = :LN_BOBYQA, solver = :Bootstrap, hmax::Float64 = 20.0, kw...)
```

制御チャート `CH` の設計を指定された最適化アルゴリズムを使用して最適化します。

### 引数

  * `CH::ControlChart`: 最適化する制御チャートオブジェクト。
  * `rlsim_oc::Function`: 制御チャートの異常状態をシミュレートする関数。
  * `settings::OptSettings`: 最適化ルーチンを制御する最適化設定（デフォルト: `OptSettings(CH)`）。

### キーワード引数

  * `optimizer::Symbol`: 使用する最適化アルゴリズム（デフォルト: `:Grid`）。
  * `solver::Symbol`: 制御限界推定に使用するルート探索アルゴリズム（デフォルト: `:Bootstrap`）。
  * `hmax::Float64`: 制御限界の最大値で、ソルバーが `:Bisection` に設定されているときのみ使用されます（デフォルト: 100.0）
  * `kw...`: ソルバーアルゴリズムに渡す追加のキーワード引数。

# 戻り値

制御チャートの最適化された設計パラメータ。
