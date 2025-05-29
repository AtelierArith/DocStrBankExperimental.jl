```
load_geometry(filename; element_type=Float64)
```

ファイルをロードし、[`ComplexShape`](@ref)に対応する型を返します。サポートされているファイル形式は`.stl`と`.asc`です。

# 引数

  * `filename`: ロードするファイルの名前。

# キーワード

  * `element_type`: 要素の型（デフォルトは`Float64`）
