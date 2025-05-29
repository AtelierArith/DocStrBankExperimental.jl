解決策の試行後のJuMPの終了ステータスと、成功した場合の解決策を保持します。

# フィールド

  * `jumpTerminationStatus`: 解決策の試行の結果を示す`JuMP.termination_status`の最終出力。
  * `z::Matrix{T}`: 成功した場合の解決策におけるセルの色の空間配列（型`T`）。
  * `palette::P`: 可能なセルの色のコレクション（各型`T`）。色の欠如は`zero(T)`として示されます。
