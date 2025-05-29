```
get_circuit(circuit::Vector{Layer}, layer_types::Vector{Symbol}, layer_times::Vector{Float64}, noise_param::AbstractNoiseParameters; kwargs...)
```

与えられた回路とノイズパラメータに基づいて [`Circuit`](@ref) オブジェクトを返します。

# 引数

  * `circuit::Vector{Layer}`: 回路。
  * `layer_types::Vector{Symbol}`: 回路内の層のタイプ。
  * `layer_times::Vector{Float64}`: 回路内の各層を実装するのにかかる時間、測定およびリセットの時間も含む。
  * `noise_param::AbstractNoiseParameters`: 回路のノイズパラメータ。

# キーワード引数

  * `circuit_param::AbstractCircuitParameters = EmptyCircuitParameters()`: 回路パラメータ。
  * `extra_fields::Dict{Symbol, Any} = Dict{Symbol, Any}()`: [`CodeParameters`](@ref) 用を含む追加フィールド。
  * `noisy_prep::Bool = false`: 準備をノイズのあるものとして扱い、関連するノイズを特定するかどうか; `noisy_prep` と `noisy_meas` の両方が `true` の場合、フルランクデザインは生成できません。
  * `noisy_meas::Bool = true`: 測定をノイズのあるものとして扱い、関連するノイズを特定するかどうか; `noisy_prep` と `noisy_meas` の両方が `true` の場合、フルランクデザインは生成できません。
  * `combined::Bool = haskey(noise_param.params, :combined) ? noise_param.params[:combined] : false,`: Pauli X, Y, Z 基底の SPAM ノイズを同じものとして扱うかどうか。
  * `strict::Bool = false`: どのゲートが相対精度で推定可能と見なされるかについて厳密であるかどうか。
