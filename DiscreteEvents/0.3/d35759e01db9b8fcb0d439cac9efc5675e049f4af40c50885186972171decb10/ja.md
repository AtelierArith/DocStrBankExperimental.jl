```
resetClock!(clk::Clock, Δt::T=0.01; t0::U=0; <keyword arguments>) where {T<:Number, U<:Number}
```

時計をリセットします。

# 引数

  * `clk::Clock`
  * `Δt::T=0.01`: サンプリングレート
  * `t0::Float64=0` または `t0::Time`: 開始時間
  * `hard::Bool=true`: 時間がリセットされ、すべてのスケジュールされたイベントとサンプリングが削除されます。もし `hard=false` の場合、時間のみがリセットされ、イベントとサンプリングの時間がそれに応じて調整されます。
  * `unit=NoUnits`: リセット後の時計の時間単位。もし `Δt::Time` が与えられた場合、その時間単位が時計の時間単位に入ります。もし `t0::Time` のみが与えられた場合、その時間単位が時計の時間単位に入ります。

# 例

```jldoctest
julia> using DiscreteEvents, Unitful

julia> import Unitful: s

julia> c = Clock(1s, t0=60s)
Clock 1: state=:idle, t=60.0s, Δt=1.0s, prc:0
  scheduled ev:0, cev:0, sampl:0

julia> resetClock!(c)
"clock reset to t₀=0.0, sampling rate Δt=0.01."

julia> c
Clock 1: state=:idle, t=0.0, Δt=0.01, prc:0
  scheduled ev:0, cev:0, sampl:0
```
