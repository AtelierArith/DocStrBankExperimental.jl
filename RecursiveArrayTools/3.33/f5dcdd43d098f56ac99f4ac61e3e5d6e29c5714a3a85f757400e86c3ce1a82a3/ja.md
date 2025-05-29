```
NamedArrayPartition(; kwargs...)
NamedArrayPartition(x::NamedTuple)
```

`ArrayPartition`に似ていますが、個々の配列はコンストラクタで指定された名前を介してアクセスできます。しかし、`ArrayPartition`とは異なり、各個別の配列は同じ要素型でなければなりません。
