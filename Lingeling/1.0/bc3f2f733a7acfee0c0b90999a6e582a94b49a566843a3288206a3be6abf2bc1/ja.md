```
lgl_defopt(solver::LglPtr, opt::String)::Cint
```

デフォルトオプションの値を取得します。

# 引数

  * `solver::LglPtr`: Lingeling SAT-Solverへのポインタ。
  * `opt::String`: オプション名。

# 戻り値

  * `val::Cint`: 指定されたオプションのデフォルトオプション値。
