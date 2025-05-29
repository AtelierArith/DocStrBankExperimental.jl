```
lazy_map(f,::Type{T},a::AbstractArray...) where T
```

[`lazy_map(f,a::AbstractArray...)`](@ref)と同様ですが、ユーザーが結果の配列の要素型を提供することで型推論を回避します。
