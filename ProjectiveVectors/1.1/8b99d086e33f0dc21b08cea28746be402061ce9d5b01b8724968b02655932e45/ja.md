```
LinearAlgebra.dot(v::PVector{T, N}, w::PVector{T2, N}) where {T, T2, N}
```

成分ごとのドット積を計算します。`@inbounds`で装飾されている場合、`v`と`w`の[`dims`](@ref)のチェックはスキップされます。
