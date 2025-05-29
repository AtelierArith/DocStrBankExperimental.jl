```
add_channel!(grid::SpmGrid, name::AbstractString, unit::AbstractString,
    data::AbstractArray{Float64}; force::Bool=false)::Nothing::Nothing
```

`name`、`unit`、および `data` を持つ生成されたチャネルを `grid` に追加します。`data` は `grid` のチャネルデータと同じサイズでなければなりません。すなわち、`grid.points` x `grid.pixelsize...` です。`name` は元のチャネル名と同じであってはなりません。生成されたチャネル名に `name` が存在する場合、それは上書きされます。`force` が `true` の場合、名前と次元の整合性チェックはオーバーライドされます。
