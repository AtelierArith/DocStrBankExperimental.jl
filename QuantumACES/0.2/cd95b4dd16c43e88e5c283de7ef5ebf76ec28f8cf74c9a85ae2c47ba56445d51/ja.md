```
回路
```

回路情報、ノイズパラメータを含む。

# フィールド

  * `circuit_param::AbstractCircuitParameters`: 回路パラメータ。
  * `circuit::Vector{Layer}`: 回路。
  * `circuit_tuple::Vector{Int}`: 回路層の順序を配置するタプル; これは初期化時に自明です。
  * `qubit_num::Int`: 回路内のキュービットの数。
  * `unique_layer_indices::Vector{Int}`: 回路のユニークな非測定ゲート層インデックス。
  * `layer_types::Vector{Symbol}`: 回路内の層のタイプ、層の時間と動的デカップリングに使用されます。
  * `layer_times::Vector{Float64}`: 回路内の各層を実装するのにかかる時間、測定およびリセットも含む。
  * `gates::Vector{Gate}`: タプルによって配置された回路内のゲート。
  * `total_gates::Vector{Gate}`: 回路内の総ゲート、`noisy_prep`の場合は準備を、`noisy_meas`の場合は測定を含む。
  * `gate_data::GateData`: 回路のゲートデータ。
  * `noise_param::AbstractNoiseParameters`: ノイズパラメータ。
  * `gate_probabilities::Dict{Gate, Vector{Float64}}`: 各ゲートのパウリ誤差確率を辞書として保存。
  * `gate_eigenvalues::Vector{Float64}`: 各ゲートの固有値、`total_gates`のゲート順序によって決定され、`gate_data`でインデックス付けされたベクトルとして保存。
  * `noisy_prep::Bool`: 準備をノイズのあるものとして扱い、関連するノイズを特性化するかどうか、デフォルトは`false`です; `noisy_prep`と`noisy_meas`の両方が`true`の場合、フルランクデザインは生成できません。
  * `noisy_meas::Bool`: 測定をノイズのあるものとして扱い、関連するノイズを特性化するかどうか、デフォルトは`true`です; `noisy_prep`と`noisy_meas`の両方が`true`の場合、フルランクデザインは生成できません。
  * `extra_fields::Dict{Symbol, Any}`: 回路の追加データ、コードパラメータを含む、症候抽出回路のための`:code_param`フィールドとして保存された[`CodeParameters`](@ref)オブジェクト。
