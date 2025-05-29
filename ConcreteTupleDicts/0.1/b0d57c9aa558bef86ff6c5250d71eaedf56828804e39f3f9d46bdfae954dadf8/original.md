```
struct TupleDict{TD, K, V} <: AbstractDict{K, V}
```

A `Dict`-like structure which maps keys of various types to values of various types     in a type stable manner. Crucially, for every key of type `TK`, it must map to     a value of type `TV`. 

With a traditional `Dict`, keys of distinct types mapping to values of distinct types     cannot lead to type stable retrieval. However, a `TupleDict` is type stable,      even when the `valtype` for each `keytype` is different.
