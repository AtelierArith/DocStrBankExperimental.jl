```
TaylorFourierTransform.tft(s::Vector{<:Number}, t::Vector{<:Number}, h::Vector{<:Int}, D::Int, F::Real, K::Int)
```

入力:

  * `s::Vector{<:Number}` | 離散信号 [?]
  * `t::Vector{<:Number}` | 離散時間 [s]
  * `h::Vector{<:Int}`    | 調和数 [-]
  * `D::Int`              | 導関数の最大次数 [-]
  * `F::Real`             | 基本周波数 [Hz]
  * `K::Int`              | oスプラインの次数 [-]

出力:

  * `sol::DTFTSolution`   | DTFTソリューション構造体

```
