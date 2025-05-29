```
AbstractCircuit
```

回路はサブタイプ `T <: AbstractCircuit` に格納され、[`get_circuit`](@ref) のメソッドによって生成されるべきです。

# 必要なフィールド

  * `circuit_param::AbstractCircuitParameters`: 回路パラメータ。
  * `circuit::Vector{Layer}`: 回路。
  * `circuit_tuple::Vector{Int}`: 回路層の順序を配置するタプル; これは初期化時に自明です。
  * `qubit_num::Int`: 回路内のキュービットの数。
  * `unique_layer_indices::Vector{Int}`: 回路のユニークな非測定ゲート層インデックス。
  * `layer_types::Vector{Symbol}`: 回路内の層のタイプ、層の時間と動的デカップリングに使用されます。
  * `layer_times::Vector{Float64}`: 回路内の各層を実装するのにかかる時間、測定およびリセットも含む。
  * `gates::Vector{Gate}`: タプルによって配置された回路内のゲート。
  * `total_gates::Vector{Gate}`: 回路内の総ゲート、`noisy_prep` の場合は準備を、`noisy_meas` の場合は測定を含む。
  * `gate_index::Dict{Gate, Int}`: 元の回路内の各ゲートの固有値のインデックス。
  * `N::Int`: ゲート固有値の数。
  * `marginal_gate_index::Dict{Gate, Int}`: 元の回路内の各ゲートの周辺ゲート固有値のインデックス、周辺は[`get_orbit_indices_dict`](@ref)で指定されたパウリ軌道によって決定されます。
  * `N_marginal::Int`: 周辺ゲート固有値の数。
  * `N_relative::Int`: 相対ゲート固有値の数。
  * `noise_param::AbstractNoiseParameters`: ノイズパラメータ。
  * `gate_probabilities::Dict{Gate, Vector{Float64}}`: 各ゲートのパウリエラー確率を辞書として保存。
  * `gate_eigenvalues::Vector{Float64}`: 各ゲートの固有値を、`gate_index` によって決定される順序のベクトルとして保存。
  * `marginal_gate_probabilities::Dict{Gate, Vector{Float64}}`: 各ゲートの周辺パウリエラー確率を辞書として保存。
  * `marginal_gate_eigenvalues::Vector{Float64}`: 各ゲートの周辺固有値を、`marginal_gate_index` によって決定される順序のベクトルとして保存。
  * `relative_gate_eigenvalues::Vector{Float64}`: 周辺固有値が相対精度で推定できる各ゲートの周辺固有値、すなわち準備または測定でないものを、`marginal_gate_index` によって決定される順序のベクトルとして保存。
  * `noisy_prep::Bool`: 準備をノイズありとして扱い、関連するノイズを特徴付けるかどうか、デフォルトは `false` であるべきです; `noisy_prep` と `noisy_meas` の両方が `true` の場合、フルランクデザインは生成できません。
  * `noisy_meas::Bool`: 測定をノイズありとして扱い、関連するノイズを特徴付けるかどうか、デフォルトは `true` であるべきです; `noisy_prep` と `noisy_meas` の両方が `true` の場合、フルランクデザインは生成できません。
  * `extra_fields::Dict{Symbol, Any}`: 回路のための追加データ、コードパラメータを含む、これは `:code_param` フィールドとして保存される [`CodeParameters`](@ref) オブジェクトです。
