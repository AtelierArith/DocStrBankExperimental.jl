MCNoGrad(y::Interval{Float64})

`y.lo` に等しい凸緩和と `y.hi` に等しい凹緩和を持つ McCormick 緩和を構築します。
