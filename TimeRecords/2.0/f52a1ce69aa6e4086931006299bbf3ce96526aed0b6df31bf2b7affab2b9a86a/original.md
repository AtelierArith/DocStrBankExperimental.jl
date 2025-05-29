AbstractTimeSeries{T} <: AbstractVector{TimeRecord{T}}

A sorted AbstractVector{TimeRecord{T}}, in ascending order by timestamp All children of AbstractTimeSeries must support the 'records(ts)' function By default, records(ts::AbstractTimeSeries) = ts.records
