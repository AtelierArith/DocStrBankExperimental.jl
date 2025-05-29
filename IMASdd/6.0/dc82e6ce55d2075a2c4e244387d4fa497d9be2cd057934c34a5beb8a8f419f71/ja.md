```
Base.diff(
    @nospecialize(ids1::T),
    @nospecialize(ids2::T);
    tol::Float64=1E-2,
    recursive::Bool=true,
    verbose::Bool=false) where {T<:IDS}
```

2つのIDSを比較し、違いを持つ辞書を返します

注意: この関数は式を評価しません（値を比較するには、IDSに対して`freeze()`を使用してください）
