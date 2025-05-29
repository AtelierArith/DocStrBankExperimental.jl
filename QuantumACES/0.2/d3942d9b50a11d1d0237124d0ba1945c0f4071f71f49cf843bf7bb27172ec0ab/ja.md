```
MemorySummary
```

Stimメモリシミュレーションの要約結果。

# フィールド

  * `circuit_param::AbstractCircuitParameters`: 回路パラメータ。
  * `noise_param::AbstractNoiseParameters`: ノイズパラメータ。
  * `rounds::Int`: メモリ回路のラウンド数。
  * `shots::Int`: サンプリングされたショット数。
  * `seed::UInt64`: Stimシミュレーションのシード。
  * `reset_type::Symbol`: リセットタイプ。デフォルトは `:meas_reset` ですが、 `:meas` に設定することもできます。
  * `decoder_type::Symbol`: デコーダタイプ。デフォルトは `:pymatching` ですが、 `:beliefmatching` に設定することもできます。
  * `decoder_labels::Vector{String}`: デコーダゲート確率のラベル。
  * `memory_x_errors::Vector{Float64}`: Xメモリ実験のエラー率。
  * `memory_z_errors::Vector{Float64}`: Zメモリ実験のエラー率。
  * `memory_x_errors_cov::Matrix{Float64}`: Xメモリ実験のエラー率の共分散。
  * `memory_z_errors_cov::Matrix{Float64}`: Zメモリ実験のエラー率の共分散。
  * `change_x_errors::Matrix{Float64}`: 異なるゲート確率におけるXメモリ実験のエラー率の変化。
  * `change_z_errors::Matrix{Float64}`: 異なるゲート確率におけるZメモリ実験のエラー率の変化。
  * `change_x_errors_sem::Matrix{Float64}`: 異なるゲート確率におけるXメモリ実験のエラー率の変化の標準誤差。
  * `change_z_errors_sem::Matrix{Float64}`: 異なるゲート確率におけるZメモリ実験のエラー率の変化の標準誤差。
  * `decoder_x_confusion::Matrix{Int}`: Xメモリ実験のデコーダ混同行列。
  * `decoder_z_confusion::Matrix{Int}`: Zメモリ実験のデコーダ混同行列。
