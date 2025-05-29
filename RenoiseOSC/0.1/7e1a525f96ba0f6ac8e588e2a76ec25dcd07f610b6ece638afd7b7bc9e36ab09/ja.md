```
midievent(portid::UInt8, status::UInt8, data1::UInt8, data2::UInt8)
midievent(event::Union{UInt32,UInt64,Array{<:Integer},NTuple{4,<:Integer}})
```

生のMIDIイベントを発火させます。
