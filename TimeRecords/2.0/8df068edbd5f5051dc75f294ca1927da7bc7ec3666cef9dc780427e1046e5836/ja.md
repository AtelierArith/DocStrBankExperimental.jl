findinner(ts::AbstractTimeSeries, Δt::TimeInterval, indhint::Base.RefValue{<:Integer})

時間系列 (ts) のインデックスを見つけます (Δt[begin] <= ts.t <= Δt[end])。将来の使用のためにインデックス範囲の最後の値を保存します。
