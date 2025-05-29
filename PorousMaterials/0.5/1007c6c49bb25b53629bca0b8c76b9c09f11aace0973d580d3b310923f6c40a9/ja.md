```
grid = read_cube(filename)
```

.cubeファイルを読み込み、 populated `Grid`データ構造を返します。ファイルに原子情報が含まれている場合は、それを検出してスキップします。

# 引数

  * `filename::AbstractString`: グリッドを書き込む.cubeファイルの名前; これは`rc[:paths][:grids]`に対して相対的です
  * `has_units::Bool=true`: ファイルヘッダーから単位を読み取るためのフラグ

# 戻り値

  * `grid::Grid`: グリッドデータ構造
