```
lgl_hasopt(solver::LglPtr, opt::String)::Cint
```

オプションが存在するかどうかを確認します。

# 引数

  * `solver::LglPtr`: Lingeling SAT-Solverへのポインタ。
  * `opt::String`: オプション名。

# 戻り値

  * `val::Cint`: オプションが存在するかどうか。存在する場合は`1`、そうでない場合は`0`。
