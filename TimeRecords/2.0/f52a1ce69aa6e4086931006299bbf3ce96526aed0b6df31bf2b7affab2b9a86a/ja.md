AbstractTimeSeries{T} <: AbstractVector{TimeRecord{T}}

タイムスタンプで昇順にソートされた AbstractVector{TimeRecord{T}}。AbstractTimeSeries のすべての子は 'records(ts)' 関数をサポートする必要があります。デフォルトでは、records(ts::AbstractTimeSeries) = ts.records です。
