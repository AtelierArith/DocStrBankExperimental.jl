```
lgl_melt(solver::LglPtr, lit::Integer)
```

リテラルを溶かすことは、`lgl_sat`中に削除される可能性があることを意味します。

# 引数

  * `solver::LglPtr`: Lingeling SAT-Solverへのポインタ。
  * `lit::Integer`: 溶かすリテラル。

# 例外

  * `InexactError`: リテラルが`Cint`に変換できない場合。
