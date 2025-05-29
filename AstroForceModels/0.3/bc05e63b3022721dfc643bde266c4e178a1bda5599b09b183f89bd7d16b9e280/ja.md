相対性宇宙モデル構造体は、宇宙船に作用する相対性の加速度を計算するための情報を含みます。

# フィールド

  * `central_body::ThirdBodyModel`: 中心天体の重力パラメータを計算するためのデータ。
  * `sun_body::ThirdBodyModel`: 太陽の位置、速度、および重力パラメータを計算するためのデータ。
  * `eop_data::Union{EopIau1980,EopIau2000A}`: 地球の方向パラメータデータ。
  * `c::Number`: 光の速度 [km/s]。
  * `γ::Number`: ポストニュートンパラメータ化パラメータ。一般相対性理論では γ=1。
  * `β::Number`: ポストニュートンパラメータ化パラメータ。一般相対性理論では β=1。
  * `schwartzchild_effect::Bool`: シュワルツシルト相対性効果を含める。
  * `lense_thirring_effect::Bool`: レンズ・ティリング相対性効果を含める。
  * `de_Sitter_effect::Bool`: デ・シッター相対性効果を含める。
