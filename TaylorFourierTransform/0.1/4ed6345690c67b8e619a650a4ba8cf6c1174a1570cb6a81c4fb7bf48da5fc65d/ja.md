TaylorFourierTransform.ftft(s::Vector{<:Number}, t::Vector{<:Number}, D::Int, F::Real, K::Int)

入力:

  * `s::Vector{<:Number}` | 離散信号 [?]
  * `t::Vector{<:Number}` | 離散時間 [s]
  * `D::Int`              | 導関数の最大次数 [-]
  * `F::Real`             | 基本周波数 [Hz]
  * `K::Int`              | oスプラインの次数 [-]

出力:

  * `sol::DTFTSolution`   | DTFTソリューション構造体
