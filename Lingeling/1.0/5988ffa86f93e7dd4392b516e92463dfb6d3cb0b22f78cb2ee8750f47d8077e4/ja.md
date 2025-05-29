```
lgl_setopt(solver::LglPtr, opt::String, val::Integer)
```

オプション値を設定します。

# 引数

  * `solver::LglPtr`: Lingeling SAT-Solverへのポインタ。
  * `opt::String`: オプション名。
  * `val::Integer`: 新しいオプション値。

# 例外

  * `InexactError`: オプション値が`Cint`に変換できない場合。
