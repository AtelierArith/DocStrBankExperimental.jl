```
mutable struct Simulation{S, A, VS}
```

モンテカルロシミュレーションを表す構造体です。

# フィールド

  * `chains::Vector{S}`: 独立したアリアナシステムのベクター。
  * `algorithms::A`: アルゴリズムのリスト。
  * `steps::Int`: MCスイープの数。
  * `t::Int`: 現在の時間ステップ。
  * `schedulers::VS`: スケジューラのリスト（各アルゴリズム用）。
  * `counters::Vector{Int}`: スケジューラのカウンタ（各アルゴリズム用）。
  * `path::String`: シミュレーションパス。
  * `verbose::Bool`: 詳細出力のフラグ。
