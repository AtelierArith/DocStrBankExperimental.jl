```
lgl_freeze(solver::LglPtr, lit::Integer)
```

リテラルをフリーズし、`lgl_sat`中に削除されないようにします。これにより、将来の`lgl_add`呼び出しで使用できるようになります。

# 引数

  * `solver::LglPtr`: Lingeling SAT-Solverへのポインタ。
  * `lit::Integer`: フリーズするリテラル。

# 例外

  * `InexactError`: リテラルを`Cint`に変換できない場合。
