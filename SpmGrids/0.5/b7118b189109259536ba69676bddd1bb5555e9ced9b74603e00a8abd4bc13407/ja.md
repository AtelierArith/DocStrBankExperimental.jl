```
add_parameter!(func::Function, grid::SpmGrid, name::AbstractString, unit::AbstractString,
    args...::AbstractString; force::Bool=false)::Nothing
```

`name`、`unit`、および `data` を `grid` に追加する生成されたパラメータを追加します。パラメータは、`args...` で指定された他のパラメータ/チャネルを入力パラメータとして受け取る関数 `func` によって生成されます。ブロードキャスティング機能は `func` 内で実装されるべきです。`name` は元のパラメータ名と同じであってはなりません。生成されたパラメータ名に `name` が存在する場合、それは上書きされます。`force` が `true` の場合、名前と次元の整合性チェックはオーバーライドされます。

# 例

```julia
julia> grid = load_grid("file.3ds")
julia> add_parameter!(x -> abs(x), grid, "Scan:ExcitationAbs", "V", "Scan:Excitation")
```
