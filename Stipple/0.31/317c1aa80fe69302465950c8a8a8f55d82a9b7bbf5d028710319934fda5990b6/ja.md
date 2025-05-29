```
function Stipple.render(o::Reactive{T}, fieldname::Union{Symbol,Nothing} = nothing) where {T}
```

`Reactive` 値のデフォルトレンダリング。あなたの型 `T` に対してカスタムレンダリングを定義するために `Stipple.render` を特化させてください。
