```
lgl_add(solver::LglPtr, lit::Integer)
```

次の節のリテラルを追加します。`0`リテラルは節を終了します。

# 引数

  * `solver::LglPtr`: Lingeling SAT-Solverへのポインタ。
  * `lit::Cint`: 追加するリテラル。`0`リテラルは節を終了します。負のリテラルは否定されます（つまり、`-2`は「NOT 2」を意味します）。

# 例外

  * `InexactError`: リテラルを`Cint`に変換できない場合。
