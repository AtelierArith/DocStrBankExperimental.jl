```
simulate_memory(c::AbstractCircuit, rounds::Integer, shots::Integer; kwargs...)
```

指定された症候抽出回路を用いて実施されたメモリ実験のメモリおよびデコーディングシミュレーション結果を返します。

WARNING: シードはStimと同様の機能を持っています。同じランダムシードの動作はStimの異なるバージョン間で異なります。また、測定ショットがバッチでサンプリングされる場合（`max_samples`を超えたときに発生）、すべてのショットが一度にサンプリングされたときとは結果が異なります。

# 引数

  * `c::AbstractCircuit`: 症候抽出回路。
  * `rounds::Integer`: メモリ回路のラウンド数で、0以上でなければなりません。
  * `shots::Integer`: ショット数で、1以上でなければなりません。

# キーワード引数

  * `seed::Union{UInt64, Nothing} = nothing`: ランダム数生成に使用するシード。
  * `reset_type::Symbol = :meas_reset`: リセットタイプで、`:meas_reset`または`:meas`のいずれかでなければなりません。
  * `decoder_type::Symbol = :pymatching`: デコーダタイプで、`:pymatching`または`:beliefmatching`のいずれかでなければなりません。
  * `decoder_gate_probabilities::Vector{Dict{Gate, Vector{Float64}}} = [c.gate_probabilities]`: デコーディングに使用されるゲート確率で、最初のものは提供された回路`c`のゲート確率でなければなりません。
  * `decoder_labels::Vector{String} = [string(idx) for idx in 1:length(decoder_gate_probabilities)]`: デコーダゲート確率のラベル。
  * `max_samples::Integer = 10^9`: 単一のシミュレーションで収集されるStim検出器サンプルの最大数。
  * `diagnostics::Bool = false`: 診断を印刷するかどうか。
