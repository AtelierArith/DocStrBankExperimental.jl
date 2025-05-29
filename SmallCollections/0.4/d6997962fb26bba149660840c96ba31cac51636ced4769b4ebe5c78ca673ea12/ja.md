```
empty(v::AbstractSmallVector{N}, S::Type) where {N,S} -> AbstractSmallVector{N,S}
```

空の `AbstractSmallVector` を返します。これは `v` と同じ容量を持ち、要素の型は `U` です。結果として得られるベクターは、`v` が可変である場合に限り可変です。

関連情報として [`empty(v::AbstractCapacityVector)`](@ref) を参照してください。
