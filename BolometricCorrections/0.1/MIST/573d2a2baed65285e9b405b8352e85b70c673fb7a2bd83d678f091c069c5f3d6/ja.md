```
MISTBCGrid(grid::AbstractString)
```

与えられた光度系 `grid` の MIST ボロメトリック補正をロードして返します。このタイプは、固定された従属グリッド変数（[Fe/H], Av, Rv）を持つ [`MISTBCTable`](@ref) のインスタンスを作成するために使用されます。これは、`MISTBCGrid` のインスタンスを `(feh, Av)` 引数で呼び出すか、[`MISTBCTable`](@ref) の適切なコンストラクタを使用することで行うことができます。

```jldoctest
julia> grid = MISTBCGrid("JWST")
MIST_JWST の光度系のための MIST ボロメトリック補正グリッド

julia> grid(-1.01, 0.11) # 補間された [Fe/H], Av でテーブルを構築するために呼び出すことができます
[Fe/H] -1.01 と V バンドの消光 0.11 を持つ MIST ボロメトリック補正テーブル
```
