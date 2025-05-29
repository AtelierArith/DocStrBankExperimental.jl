apply!(f::Function, collector::TimeSeriesCollector, tagrecord::Pair{<:String, <:TimeRecord}) :: Union{Nothing, Task}

Use apply!(collector, timestamp(tagrecord[2])) :: Union{Nothing, NamedTuple{snapshot<:Dict, interval::TimeInterval}}

  * If data is returned (i.e. not 'nothing') collector.data before collector.timer[] will be deleted
  * The function 'f' will be applied to 'data.snapshot, data.interval' in a separate 'Task' which is returned

Regardless of the outcome of 'apply', 'tagrecord' will be appended to collector.data

Notes:

  * The function f must accept two arguments: (data::Dict{String,<:TimeSereis}, interval::TimeInterval)
  * 'interval' will be contained inside 'data' allowing for any desired interpolation scheme
