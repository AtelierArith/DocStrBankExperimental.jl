```
LogRecordData(data)

LogRecordData(args::Pair{<:Any, <:Any}...)
```

A type representing an optional collection of `key => value` pairs attached to a log record. 

`data` must be an iterable collection where each element is a `Pair`
