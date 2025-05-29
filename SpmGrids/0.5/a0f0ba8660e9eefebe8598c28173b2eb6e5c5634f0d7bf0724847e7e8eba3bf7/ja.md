```
add_channel!(func::Function, grid::SpmGrid, name::AbstractString, unit::AbstractString,
    args...; skip_bwd::Bool=false, force::Bool=false)::Nothing
```

`name`、`unit`、および `data` を持つ生成されたチャネルを `grid` に追加します。チャネルは、`args...` で指定された他のチャネル/パラメータを入力パラメータとして受け取る関数 `func` によって生成されます。ブロードキャスティング機能は `func` 内で実装する必要があります。`name` は元のチャネル名と同じであってはなりません。生成されたチャネル名に `name` が存在する場合、それは上書きされます。`skip_bwd` が `false`（デフォルト）の場合、可能であれば bwd チャネルが追加されます。`force` が `true` の場合、名前と次元の整合性チェックはオーバーライドされます。

# 例

```julia
julia> grid = load_grid("file.3ds")
julia> add_channel!(x -> abs(x), grid, "CurrentAbs", "A", "Current")
julia> add_channel!((x,y) -> x + y, grid, "", "A", "Current", "AbsCurrent")
```
