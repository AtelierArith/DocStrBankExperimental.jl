```
mutable struct Inputs{T<:Phases} <: AbstractInputs
    edges::Array{Tuple, 1}
    linecodes::Array{String, 1}
    linelengths::Array{Float64, 1}
    busses::Array{String}
    phases::Vector{Vector}
    substation_bus::String
    Pload::Dict{String, Any}
    Qload::Dict{String, Any}
    Sbase::Real
    Vbase::Real
    Ibase::Real
    Zdict::Dict{String, Dict{String, Any}}
    v0::Real
    v_lolim::Real
    v_uplim::Real
    Zbase::Real
    Ntimesteps::Int
    pf::Float64
    Nnodes::Int
    P_up_bound::Float64
    Q_up_bound::Float64
    P_lo_bound::Float64
    Q_lo_bound::Float64
    Isquared_up_bounds::Dict{String, <:Real}
    phases_into_bus::Dict{String, Vector{Int}}
    relaxed::Bool
    edge_keys::Vector{String}
    regulators::Dict
    shunt_susceptance::Dict
end
```

Inputs

  * `edges` Vector{Tuple} 例: `[("0", "1"), ("1", "2")]`
  * `linecodes` Zdictのための文字列キーのベクター（ラインのインピーダンス値）。OpenDSSモデルを使用する場合、`linecode`は`New linecode.name`の`name`です。
  * `linelengths` インピーダンス値をスケールするための浮動小数点数のベクター
  * `busses` バス名のベクター
  * `phases` ラインフェーズのための整数のベクターのベクター（例: `[[1,2,3], [1,3], ...]`）
  * `Pload` バスをキーとし、フェーズと時間ごとの制御されていない実負荷（正は負荷）を持つ辞書
  * `Qload` バスをキーとし、フェーズと時間ごとの制御されていない無効負荷（正は負荷）を持つ辞書
  * `Sbase` ネットワークの基準見かけの電力、通常はフィーダー容量。モデル内のすべての電力を正規化するために使用されます。
  * `Vbase` ネットワークの基準電圧、`Zbase = Vbase^2 / Sbase`を決定するために使用されます。
  * `Ibase` = `Sbase / (Vbase * sqrt(3))`
  * `Zdict` `linecodes`をキーとし、"xmatrix"および"zmatrix"キーを持つサブ辞書を持つ辞書。値は`Zbase`で割られ、数学モデル内でライン長で掛けられます。
  * `v0` スラックバスの基準電圧

TODO Zdictの例

TODO スケーリングが正しく行われていることを確認するためにシンプルなモデルに対してテスト

!!! note
    `edges`、`linecodes`、`phases`、`edge_keys`、および`linelengths`は相互に順序が一致しています（すなわち、各リストのi番目の値は同じラインに対応します）

