```
NotIndex{T} <: AbstractNotIndex{T}
```

[`not`](@ref) のデフォルト実装です。`FI(!in(x))` と比較して `NotIndex(x)` にはいくつかの最適化があります。大きな配列に対しては、この実装の方が速い場合がありますが、小さな配列に対してはこの実装の方が遅くなる場合があります。詳細については [performance comparing](@ref performance) を参照してください。
