apply!(collector::TimeSeriesCollector, tagrecord::Pair{<:String, <:TimeRecord}) :: Union{Nothing, NamedTuple{snapshot<:Dict, interval::TimeInterval}}

Use 'take!(collector, timestamp(tagrecord[2]))' which returns 'Union{Nothing, NamedTuple{snapshot<:Dict, interval::TimeInterval}}'

  * If data is returned (i.e. not 'nothing') collector.data before collector.timer[] will be deleted

Regardless of the outcome of 'take', 'tagrecord' will be appended to collector.data

Notes:

  * 'interval' will be contained inside 'data' allowing for any desired interpolation scheme
