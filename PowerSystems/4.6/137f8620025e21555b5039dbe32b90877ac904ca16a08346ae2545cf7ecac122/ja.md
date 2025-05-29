```
mutable struct PeriodicVariableSource <: DynamicInjection
    name::String
    R_th::Float64
    X_th::Float64
    internal_voltage_bias::Float64
    internal_voltage_frequencies::Vector{Float64}
    internal_voltage_coefficients::Vector{Tuple{Float64,Float64}}
    internal_angle_bias::Float64
    internal_angle_frequencies::Vector{Float64}
    internal_angle_coefficients::Vector{Tuple{Float64,Float64}}
    base_power::Float64
    states::Vector{Symbol}
    n_states::Int
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

この構造体は、時間変化する位相値の大きさと角度 V(t) 	heta(t) を持つ無限バスとして機能します。時間変化する関数はフーリエ級数を使用して表現されます。

# 引数

  * `name::String`: コンポーネントの名前。同じタイプのコンポーネント（例: `PowerLoad`）は一意の名前を持たなければなりませんが、異なるタイプのコンポーネント（例: `PowerLoad` と `ACBus`）は同じ名前を持つことができます。
  * `R_th::Float64`: ソースのテブナン抵抗、検証範囲: `(0, nothing)`
  * `X_th::Float64`: ソースのテブナンリアクタンス、検証範囲: `(0, nothing)`
  * `internal_voltage_bias::Float64`: (デフォルト: `0.0`) 電圧のフーリエ級数の a0 項
  * `internal_voltage_frequencies::Vector{Float64}`: (デフォルト: `[0.0]`) 周波数（ラジアン/秒）
  * `internal_voltage_coefficients::Vector{Tuple{Float64,Float64}}`: (デフォルト: `[(0.0, 0.0)]`) n > 1 の項の係数。最初の成分は sin に対応し、2 番目の成分は cos に対応します。
  * `internal_angle_bias::Float64`: (デフォルト: `0.0`) 角度のフーリエ級数の a0 項
  * `internal_angle_frequencies::Vector{Float64}`: (デフォルト: `[0.0]`) 周波数（ラジアン/秒）
  * `internal_angle_coefficients::Vector{Tuple{Float64,Float64}}`: (デフォルト: `[(0.0, 0.0)]`) n > 1 の項の係数。最初の成分は sin に対応し、2 番目の成分は cos に対応します。
  * `base_power::Float64`: (デフォルト: `100.0`) ソースの基準電力（MVA）[単位化](@ref per_unit) のためのもの
  * `states::Vector{Symbol}`: (**変更しないでください。**) 時間、電圧、角度のための [状態](@ref S)
  * `n_states::Int`: (**変更しないでください。**) PeriodicVariableSource は 2 つの状態を持ちます。
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) シミュレーションで使用されないメタデータ（緯度や経度など）を追加するための [*ext*ra 辞書](@ref additional_fields)。
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl の内部参照
