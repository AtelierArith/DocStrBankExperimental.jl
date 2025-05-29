```
optimize_design(CH::ControlChart, rlsim_oc::Function, settings::OptSettings=OptSettings(CH); optimizer::Symbol = :LN_BOBYQA, solver::Symbol = :SACL, nsims_opt::Int = 1000, kw...)
```

指定された最適化アルゴリズムを使用して、管理図の設計を最適化します。

### 引数

  * `CH::ControlChart`: 最適化する管理図オブジェクト。
  * `rlsim_oc::Function`: 管理図の制御外状態をシミュレートする関数。
  * `settings::OptSettings`: 最適化ルーチンを制御する最適化設定（デフォルト: `OptSettings(CH)`）。

### キーワード引数

  * `optimizer::Symbol`: 使用する最適化アルゴリズム（デフォルト: `:Grid`）。
  * `solver::Symbol`: 制御限界推定に使用するルート探索アルゴリズム（デフォルト: `:Bootstrap`）。
  * `hmax::Float64`: 制御限界の最大値で、二分法アルゴリズムにのみ使用されます（デフォルト: 100.0）
  * `kw...`: ソルバーアルゴリズムに渡す追加のキーワード引数。

# 戻り値

管理図の最適化された設計パラメータ。
