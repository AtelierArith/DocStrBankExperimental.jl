```
MemoryData
```

Stimメモリシミュレーション結果。

# フィールド

  * `circuit_param::AbstractCircuitParameters`: 回路パラメータ。
  * `noise_param::AbstractNoiseParameters`: ノイズパラメータ。
  * `rounds::Int`: メモリ回路のラウンド数。
  * `shots::Int`: サンプリングされたショットの数。
  * `seed::UInt64`: Stimシミュレーションのシード。
  * `reset_type::Symbol`: リセットタイプ。デフォルトは `:meas_reset` ですが、 `:meas` に設定することもできます。
  * `decoder_type::Symbol`: デコーダタイプ。デフォルトは `:pymatching` ですが、 `:beliefmatching` に設定することもできます。
  * `decoder_gate_probabilities::Vector{Dict{Gate, Vector{Float64}}}`: デコーダに情報を提供するために使用されるゲート確率のベクター。
  * `decoder_labels::Vector{String}`: `decoder_gate_probabilities` のゲート確率のラベル。
  * `memory_x_observable::Vector{Bool}`: 各ショットにわたるXメモリ実験の可観測量。
  * `memory_z_observable::Vector{Bool}`: 各ショットにわたるZメモリ実験の可観測量。
  * `decoder_x_predictions::Matrix{Bool}`: `decoder_gate_probabilities` の各ショットおよびデコーダにわたるXメモリ実験のデコーダ予測。
  * `decoder_z_predictions::Matrix{Bool}`: `decoder_gate_probabilities` の各ショットおよびデコーダにわたるZメモリ実験のデコーダ予測。
