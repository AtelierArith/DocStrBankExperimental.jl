```
evolve!(model, tspan; dt, method, output)
```

モデルの進化を時間にわたってシミュレートし、必要に応じてデータを収集します。

# 引数

  * `model::Model`: 現在の状態と状態の変化率を記述する離散化されたプロセスを含む[`Model`](@ref)。
  * `tspan`: モデルの進化をシミュレートする時間範囲。総期間を持つ単一の`Number`または開始時刻と終了時刻を持つ`Number`の`Tuple`であることができます。

# キーワード

  * `dt`: 時間ステップの（定数）サイズ（必須）。`tspan`は`dt`で割り切れる必要があります。
  * `method = SSPRK33()`: 半離散初期値問題を常微分方程式として解くために使用される[時間積分法](@ref Time-Integration-Methods)。
  * `output = []`: シミュレーション中にデータを収集する[出力モジュール](@ref Output-Modules)のリスト。
