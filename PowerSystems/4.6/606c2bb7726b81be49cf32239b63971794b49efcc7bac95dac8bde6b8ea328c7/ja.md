```
mutable struct SCRX <: AVR
    Ta_Tb::Float64
    Tb::Float64
    K::Float64
    Te::Float64
    Efd_lim::MinMax
    switch::Int
    rc_rfd::Float64
    V_ref::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    states_types::Vector{StateTypes}
    internal::InfrastructureSystemsInternal
end
```

この励磁装置はIEEEタイプSCRXの固体励磁装置に基づいています。出力フィールド電圧は、システム電圧をVrefに維持するために制御システムによって変化します。この励磁装置モデルには初期化機能がないことに注意してください。これは、機械モデルの状態に関係なく、受け取った入力に応じて応答することを意味します。

# 引数

  * `Ta_Tb::Float64`: リード入力定数比、検証範囲: `(0.05, 0.3)`
  * `Tb::Float64`: ラグ入力定数（秒）、検証範囲: `(5, 20)`
  * `K::Float64`: 調整器ゲイン、検証範囲: `(20, 100)`
  * `Te::Float64`: 調整器時間定数、検証範囲: `(0, 1)`
  * `Efd_lim::MinMax`: フィールド電圧調整器の制限（調整器出力）（Efd*min, Efd*max）
  * `switch::Int`: スイッチ、検証範囲: `(0, 1)`
  * `rc_rfd::Float64`: フィールド電流能力。負の電流能力の場合は0に設定。典型的な値は10、検証範囲: `(0, 10)`
  * `V_ref::Float64`: （デフォルト: `1.0`）基準電圧設定値（pu）、検証範囲: `(0, nothing)`
  * `ext::Dict{String, Any}`: （デフォルト: `Dict{String, Any}()`）シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度。
  * `states::Vector{Symbol}`: (**変更しないでください。**) [状態](@ref S)は：

```
Vr1: 最初の積分器,
Vr2: 第二の積分器
```

  * `n_states::Int`: (**変更しないでください。**) SCRXは2つの状態を持ちます
  * `states_types::Vector{StateTypes}`: (**変更しないでください。**) SCRXは2つの[differential](@ref states_list) [状態](@ref S)を持ちます
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl内部参照
