Cross_Sections

マルチグループ交差断面ライブラリを抽出または構築するためのパラメータを定義するために使用される構造体。

# 必須フィールド

  * `source::String` : 交差断面のソース。
  * `materials::Vector{Material}` : 材料リスト。
  * **if `source = "fmac-m"`**

      * `file::String` : 交差断面データを含むファイル。
  * **if `source = "physics-models"`**

      * `particles::Vector{String}` : 粒子リスト。
      * `energy::Float64` : 最高エネルギーグループの中間エネルギー [MeV単位]。
      * `number_of_groups::Int64` : エネルギーグループの数。
      * `group_structure::String="log"` : グループ離散化のタイプ。
      * `legendre_order::Int64` : 微分交差断面の角度レジャンドルモーメントの最大次数。
      * `interactions::Vector{Interaction}` : 相互作用のリスト。
  * ** if `source = "custom"`**

      * `particles::Vector{String}` : 粒子リスト。

# オプションフィールド - デフォルト値付き

  * **if `source = "physics-models"`**

      * `cutoff::Float64 = 0.001` : 最低エネルギーグループの下限エネルギー（カットオフエネルギー） [MeV単位]。
  * ** if `source = "custom"`**

      * `custom_absorption::Vector{Real}` : 材料ごとの吸収交差断面。
      * `custom_scattering::Vector{Real}` : 材料ごとの散乱（等方的）交差断面。
