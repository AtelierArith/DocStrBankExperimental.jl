```
MISTBCTable(grid::MISTBCGrid, feh::Real, Av::Real)
```

`grid`内のMISTボロメトリック補正を、固定値の[Fe/H]（`feh`）とVバンドの消光（`Av`）に補間し、`Teff`と`logg`のみを従属変数として残します（MIST BCには1つの`Rv`値しかありません）。温度と表面重力の関数としてボロメトリック補正を補間するために、引数`(Teff, logg)`で呼び出すことができるインスタンスを返します。

```jldoctest
julia> grid = MISTBCGrid("JWST")
MIST_JWSTフォトメトリックシステムのMISTボロメトリック補正グリッド

julia> table = MISTBCTable(grid, -1.01, 0.011)
[Fe/H] -1.01およびVバンド消光0.011のMISTボロメトリック補正テーブル

julia> length(table(2755, 0.01)) == 29 # 各フィルターのBCを返します
true
```
