```julia
writeVTK(
    filename::String,
    grid::ExtendableGrids.ExtendableGrid{Tc, Ti};
    append,
    compress,
    kwargs...
) -> Vector{String}

```

グリッドとオプションで提供されたデータをvtkファイルとしてエクスポートします。

  * `filename`: エクスポートされるファイルのファイル名
  * `grid`: グリッド

各 '(key, value)' ペアは、WriteVTK機能を介してvtkファイルに別のデータエントリを追加します。

引数 'append' と 'compress' については、WriteVTKのvtk_gridのドキュメントを参照してください。
