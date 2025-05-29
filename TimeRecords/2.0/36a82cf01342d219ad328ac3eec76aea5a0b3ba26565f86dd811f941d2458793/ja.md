findouter(ts::AbstractTimeSeries, Δt::TimeInterval, indhint::Base.RefValue{<:Integer})

時間間隔Δtを囲むTimeSeries tsのインデックスを見つけ、将来の使用のためにその値をindhintに格納します。
