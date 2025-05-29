```
struct StableExtractor{T <: LeafExtractor} <: LeafExtractor
```

他の`LeafExtractor`をラップし、欠損入力値に対して安定した結果を出力するようにします。

参照: [`stabilizeextractor`](@ref).
