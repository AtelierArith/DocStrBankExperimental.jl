```
ContinuousAgent{D,T} <: AbstractAgent
```

`D`次元の [`ContinuousSpace`](@ref) で使用するための最小限のエージェント構造体です。追加のフィールド `pos::SVector{D,T}, vel::SVector{D,T}` を持ち、ここで `T` は任意の `AbstractFloat` 型です。詳細は [`@agent`](@ref) を参照してください。
