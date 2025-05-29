```
empty(v::PackedVector{U,M}, S::Type) where {U,M,S} -> PackedVector{U,M,S}
```

同じビットマスクタイプと同じビットサイズを持つ空の `PackedVector` を返しますが、要素タイプは `S` です。

関連情報として [`empty(v::AbstractCapacityVector)`](@ref) を参照してください。
