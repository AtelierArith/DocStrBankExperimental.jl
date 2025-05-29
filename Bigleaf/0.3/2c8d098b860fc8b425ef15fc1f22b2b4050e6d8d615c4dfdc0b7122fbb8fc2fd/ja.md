```
aerodynamic_conductance!(df; 
  Gb_model = Thom1972(), Ram_model = ResistanceWindZr(),
  zr=nothing, zh=nothing, d = isnothing(zh) ? nothing : 0.7*zh,
  ...
  )
```

バルク空気力学的伝導率、境界層伝導率の定式化および安定性補正関数のオプションを含む。

# 引数

  * `df`: 列を持つDataFrame

      * `ustar`     : 摩擦速度 (m s-1)
      * `wind`      : センサー高さでの風速 (m s-1)
  * `Gb_model`  : 境界層伝導率を計算するためのモデル (see [`compute_Gb!`](@ref))
  * `Ram_model` : 空気力学的抵抗を計算するためのモデル (see [`compute_Ram`](@ref))
  * `zh`        : キャノピーの高さ (m)
  * `zr`        : 計器（基準）高さ (m)

`df`のさらなる必要な列およびキーワード引数は、`Gb_model` (see [`compute_Gb!`](@ref)) および `Ram_model` (see [`compute_Ram`](@ref)) に依存します。

`ustar` と `wind` の列のみが利用可能な場合は、デフォルトモデル (`Thom1972()` および `ResistanceWindZr()`) を使用してください。

# 詳細

熱のための空気力学的伝導率 (Ga_h) は次のように計算されます：

$$
Ga_h = 1 / (Ra_m + Rb_h)
$$

ここで、$Ra_m$ は運動量のための空気力学的抵抗であり、$Rb_h = 1/Gb_h$ は熱のための（準層流）キャノピー境界層抵抗（「過剰抵抗」）です。

`Ra_m` は [`compute_Ram`](@ref) を使用してモデル `Ram_model` で計算および説明されます。

`Rb_h` は与えられた `Gb_model` を使用して 1/[`compute_Gb!`](@ref) で計算および説明されます。

# 値

[`compute_Gb!`](@ref) の結合結果と 

  * `Ra_m`: 運動量移動のための空気力学的抵抗 (s m-1)
  * `Ga_m`: 運動量移動のための空気力学的伝導率 (m s-1)
  * `Ga_h`: 熱移動のための空気力学的伝導率 (m s-1)
  * `Ra_h`: 熱移動のための空気力学的抵抗 (s m-1)
  * `Ga_CO2`: CO2移動のための空気力学的伝導率 (m s-1)
  * `z0h`: 熱のための粗さ長 (m)

# 注

水と熱のための粗さ長 (z0h) は [`roughness_length_heat`](@ref) によって計算されます。

TODO 入力変数（LAI、Dl、または zh）は定数であるか、時間とともに変化する可能性があり、すなわち `df` と同じ長さのベクトルであることを確認してください。

水蒸気移動に対する境界層伝導率 (`Gb_w`) は、しばしば `Gb_h` と等しいと仮定されます。この仮定は、例えば関数 [`surface_conductance`](@ref) において `Bigleaf.jl` でも行われています。

運動量のための粗さ長 (`z0m`) が入力として提供されていない場合、[`roughness_parameters`](@ref) を使用して推定され、全期間にわたる単一の `z0m` 値が推定されます。季節や年ごとに変化する `z0m` 値が必要な場合は、`z0m` を入力引数として提供する必要があります。

# 例

```jldoctest; output = false
using DataFrames
df = DataFrame(Tair=25.0,pressure=100.0,wind=[3.0,4,5],
  ustar=[0.5,0.6,0.65],H=[200.0,230,250])   
# Ga の簡単な計算  
aerodynamic_conductance!(df;Gb_model=Thom1972()) 
# 対数風速プロファイルから導出されたモデルを使用した Ram の計算
aerodynamic_conductance!(df;Gb_model=Thom1972(),Ram_model = ResistanceWindProfile(), 
  zr=40,zh=25,d=17.5,z0m=2) 
# 物理に基づくキャノピー境界層モデルを使用した Ga の簡単な計算
aerodynamic_conductance!(df,Gb_model=Su2001(),
  zr=40,zh=25,d=17.5,Dl=0.05,N=2,fc=0.8)
all(isfinite.(df.psi_h))
# 出力
true
```
