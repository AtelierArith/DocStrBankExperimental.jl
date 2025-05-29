```
add_parameter!(grid::SpmGrid, name::AbstractString, unit::AbstractString,
    data::AbstractArray{Float64}; force::Bool=false)::Nothing
```

`name`、`unit`、および `data` を持つ生成されたパラメータを `grid` に追加します。`data` は `grid` のパラメータデータと同じサイズでなければなりません。すなわち、`grid.pixelsize` と同じです。`name` は元のパラメータ名のいずれとも同じであってはなりません。もし `name` が生成されたパラメータ名に存在する場合、それは上書きされます。`force` が `true` の場合、名前と次元の整合性チェックはオーバーライドされます。
