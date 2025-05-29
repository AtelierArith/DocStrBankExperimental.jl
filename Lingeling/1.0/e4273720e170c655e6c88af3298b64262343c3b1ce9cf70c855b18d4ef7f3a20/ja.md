```
lgl_frozen(solver::LglPtr, lit::Integer)::Cint
```

リテラルが凍結されているかどうかを確認します。

# 引数

  * `solver::LglPtr`: Lingeling SAT-Solverへのポインタ。
  * `lit::Integer`: 確認するリテラル。

# 戻り値

  * `val::Cint`: リテラルが凍結されているかどうか。凍結されていれば`1`、そうでなければ`0`。

# 例外

  * `InexactError`: リテラルを`Cint`に変換できない場合。
