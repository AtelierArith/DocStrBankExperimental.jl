```
mutable struct AGC <: Service
    name::String
    available::Bool
    bias::Float64
    K_p::Float64
    K_i::Float64
    K_d::Float64
    delta_t::Float64
    area::Union{Nothing, Area}
    initial_ace::Float64
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

システムまたはシステム内の特定の `Area` のための自動生成制御 (AGC)。

このモデルは比例–積分–微分 (PID) 制御を使用して、AGC のエリア制御誤差 (ACE) に対する「スムーズな」応答をシミュレートします。["大規模再生可能エネルギー浸透研究のためのAGCシミュレーションモデル。"](https://doi.org/10.1109/NAPS50074.2021.9449687) を参照してください。

# 引数

  * `name::String`: コンポーネントの名前。同じタイプのコンポーネント (例: `PowerLoad`) はユニークな名前を持たなければなりませんが、異なるタイプのコンポーネント (例: `PowerLoad` と `ACBus`) は同じ名前を持つことができます。
  * `available::Bool`: コンポーネントが接続されてオンラインであるか (`true`) 、または切断されてオフラインまたはダウンしているか (`false`) を示すインジケーター。利用できないコンポーネントはシミュレーション中に除外されます。
  * `bias::Float64`: エリア周波数バイアス (MW/Hz)
  * `K_p::Float64`: PID比例定数
  * `K_i::Float64`: PID積分定数
  * `K_d::Float64`: PID微分定数
  * `delta_t::Float64`: PID離散化期間 [秒]
  * `area::Union{Nothing, Area}`: (デフォルト: `nothing`) AGC によって制御されるエリア
  * `initial_ace::Float64`: (デフォルト: `0.0`) ACE の初期条件
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) シミュレーションで使用されないメタデータを追加するための [*ext*ra 辞書](@ref additional_fields) 。たとえば、緯度や経度など。
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl 内部参照
