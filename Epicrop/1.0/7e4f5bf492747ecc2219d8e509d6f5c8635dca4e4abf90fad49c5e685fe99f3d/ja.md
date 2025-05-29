```
hlipmodel(;
wth::DataFrames.AbstractDataFrame,
rhlim::Int64,
rainlim::Int64,
H0::Int64,
I0::Int64,
RcA::Matrix{Float64},
RcT::Matrix{Float64},
RcOpt::Float64,
p::Int64,
i::Int64,
Sx::Int64,
a::Float64,
RRS::Float64,
RRG::Float64,
)

天候データとそれぞれの作物病害の最適曲線値を使用して、健康-潜伏-感染-ポスト感染（HLIP）モデルを実行します。

## キーワード

  * `wth::DataFrames.AbstractDataFrame`: 以下の値を含む日次の天候データ。

      * `YYYYMMDD::Union{AbstractString, Dates.Date}`: ISO8601形式の日付、*すなわち*、YYYY-MM-DD
      * `DOY::Int64`: 年の連続日、一般に「ジュリアン日」と呼ばれる
      * `TEMP::AbstractFloat`: 平均日温度 (°C)
      * `RHUM::AbstractFloat`: 平均日相対湿度 (%)
      * `RAIN::AbstractFloat`: 平均日降雨量 (mm)
  * `emergence::Union{AbstractString, Dates.Date}`: 植物の出現が予想される日付。表1 Savary *et al.* 2012より。
  * `onset::Int64`: 出現日から病気の発症までの予想日数。表1 Savary *et al.* 2012より。
  * `duration::Int64`: シミュレーションの期間（成長期の長さ、日数）。表1 Savary *et al.* 2012より。
  * `rhlim::Int64`: 葉が濡れているかどうかを決定するための閾値（通常90%）。表1 Savary *et al.* 2012より。
  * `rainlim::Int64`: 葉が濡れているかどうかを決定するための閾値。表1 Savary *et al.* 2012より。
  * `H0::Int64`: 植物の健康なサイトの初期数。表1 Savary *et al.* 2012より。
  * `I0::Int64`: 感染サイトの初期数。表1 Savary *et al.* 2012より。
  * `RcA::Matrix{Float64}`: *Rc*（除去のために修正された基本感染率）の作物年齢修正因子。表1 Savary *et al.* 2012より。
  * `RcT::Matrix{Float64}`: *Rc*（除去のために修正された基本感染率）の温度修正因子。表1 Savary *et al.* 2012より。
  * `RcOpt::Float64`: 除去のために修正された潜在的な基本感染率。表1 Savary *et al.* 2012より。
  * `p::Int64`: 潜伏期間の長さ。表1 Savary *et al.* 2012より。
  * `Sx::Int64`: サイトの最大数。表1 Savary *et al.* 2012より。
  * `a::Float64`: 集約係数。表1 Savary *et al.* 2012より。
  * `RRS::Float64`: 生理的老化の相対速度。表1 Savary *et al.* 2012より。
  * `RRG::Float64`: 成長の相対速度。表1 Savary *et al.* 2012より。

## 出力

モデルの出力を持つ `DataFrames.AbstractDataFrame` で、以下のフィールドと値を含みます。

  * `simday::Int64`: 実行されたシミュレーションのゼロインデックス日。
  * `dates::Dates.Date`: シミュレーションの日付。
  * `sites::Float64`: "x" 日に存在するサイトの総数。
  * `latent::Float64`: "x" 日に存在する潜伏サイトの数。
  * `infectious::Float64`: "x" 日に存在する感染サイトの数。
  * `removed::Float64`: "x" 日に存在する除去されたサイトの数。
  * `senesced::Float64`: "x" 日に存在する老化したサイトの数。
  * `rateinf::Float64`: 感染の速度。
  * `rtransfer::Float64`: 潜伏サイトから感染サイトへの移行速度。
  * `rgrowth::Float64`: 健康なサイトの成長速度。
  * `rsenesced::Float64`: 健康なサイトの老化速度。
  * `diseased::Float64`: 病気のある（潜伏 + 感染 + 除去）サイトの数。
  * `intensity::Float64`: 総サイトに対する病気のあるサイトの数の割合。
  * `audpc::Float64`: シミュレーションされたシーズン全体の病気進行曲線の下の面積。
  * `lat::Float64`: `wth` オブジェクトによって提供された緯度値。
  * `lon::Float64`: `wth` オブジェクトによって提供された経度値。

## 例

フィリピン、ロスバニョス、カラバルゾンのためにNASA POWERからダウンロードして保存したデータを使用します。

```

julia julia> using Epicrop

julia> using DelimitedFiles

julia> using DataFrames

julia> data, header = readdlm(joinpath(                                 dirname(pathof(Epicrop)),                                     "..", "docs", "src", "assets",                                         "POWER*data*LB*PHI*2000_ws.csv"),                                 ',', header=true);

julia> w = DataFrame(data, vec(header));

julia> emergence = "2000-07-01";

julia> RcA = [0 0.35;             20 0.35;             40 0.35;             60 0.47;             80 0.59;             100 0.71;             120 1.0];

julia> RcT = [15 0.0;             20 0.06;             25 1.0;             30 0.85;             35 0.16;             40 0.0];

julia> bs = hlipmodel(;         wth=w,         emergence=emergence,         onset=20,         duration=120,         rhlim=90,         rainlim=5,         H0=600,         I0=1,         RcA=RcA,         RcT=RcT,         RcOpt=0.61,         p=6,         i=19,         Sx=100000,         a=1.0,         RRS=0.01,         RRG=0.1)

```
    120×16 DataFrame
    Row │ simday  dates       sites      latent    infectious  removed   senesced ⋯
        │ Int64   Date        Float64    Float64   Float64     Float64   Float64  ⋯
   ─────┼──────────────────────────────────────────────────────────────────────────
      1 │      1  2000-07-01    600.0       0.0         0.0      0.0         0.0  ⋯
      2 │      2  2000-07-02    653.64      0.0         0.0      0.0         6.0
      3 │      3  2000-07-03    712.04      0.0         0.0      0.0        12.53
      4 │      4  2000-07-04    775.617     0.0         0.0      0.0        19.65
      5 │      5  2000-07-05    844.821     0.0         0.0      0.0        27.41 ⋯
      6 │      6  2000-07-06    920.141     0.0         0.0      0.0        35.86
      7 │      7  2000-07-07   1002.11      0.0         0.0      0.0        45.06
      8 │      8  2000-07-08   1091.29      0.0         0.0      0.0        55.08
        │   ⋮         ⋮           ⋮         ⋮          ⋮          ⋮          ⋮    ⋱
    114 │    114  2000-10-22  87883.5    1038.79      454.187   70.2366  49807.5  ⋯
    115 │    115  2000-10-23  87923.0     941.617     542.256   79.3388  50695.5
    116 │    116  2000-10-24  87958.1     825.098     648.67    89.4445  51584.8
    117 │    117  2000-10-25  87988.2     686.497     775.218  101.498   52476.4
    118 │    118  2000-10-26  87594.1     959.018     936.18   101.498   53356.3  ⋯
    119 │    119  2000-10-27  87095.0    1332.85     1097.35   101.498   54232.2
    120 │    120  2000-10-28  86500.7    1797.92     1259.08   101.498   55103.2
                                                    10 columns and 105 rows omitted
```

```
