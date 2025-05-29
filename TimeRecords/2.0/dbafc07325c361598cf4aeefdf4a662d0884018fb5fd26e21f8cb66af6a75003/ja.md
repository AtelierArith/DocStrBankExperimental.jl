apply!(f::Function, collector::TimeSeriesCollector, tagrecord::Pair{<:String, <:TimeRecord}) :: Union{Nothing, Task}

Use apply!(collector, timestamp(tagrecord[2])) :: Union{Nothing, NamedTuple{snapshot<:Dict, interval::TimeInterval}}

  * データが返される場合（すなわち 'nothing' でない場合）、collector.timer[] の前の collector.data は削除されます
  * 関数 'f' は 'data.snapshot, data.interval' に対して別の 'Task' で適用され、これが返されます

'apply' の結果に関わらず、'tagrecord' は collector.data に追加されます

ノート:

  * 関数 f は二つの引数を受け入れなければなりません: (data::Dict{String,<:TimeSereis}, interval::TimeInterval)
  * 'interval' は 'data' 内に含まれ、任意の望ましい補間スキームを可能にします
