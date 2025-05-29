```
function Stipple.render(val::T, fieldname::Union{Symbol,Nothing} = nothing) where {T}
```

値型のデフォルトレンダリング。あなたの型のカスタムレンダリングを定義するために`Stipple.render`を特化させてください。
