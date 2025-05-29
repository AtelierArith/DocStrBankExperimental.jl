```
projection(red::Reduction,s::AbstractArray) -> Projection
projection(red::Reduction,s::AbstractArray,X::MatrixOrTensor) -> Projection
```

コレクションのスナップショット `s` から [`Projection`](@ref) を構築します。量 `X` で表される内積を提供することができ、その場合、結果の `Projection` は `X`-直交になります。
