```
isequispaced(t; kwargs...) → true/false
```

時間ベクトル `t` が均等に間隔を空けている場合は `true` を返します。`AbstractRange` に対しては常に真ですが、`AbstractVector` に対しては `t` の連続する差が `isapprox(; kwargs...)` と比較され、すべてがほぼ同じであれば `true` が返されます。
