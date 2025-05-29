```julia
evaluate(
    selection::Chemfiles.Selection,
    frame::Chemfiles.Frame
) -> Vector{Any}

```

与えられた `frame` に対して `selection` を評価します。この関数は、選択に一致するフレーム内の原子のインデックスまたはインデックスのタプルのリストを返します。
