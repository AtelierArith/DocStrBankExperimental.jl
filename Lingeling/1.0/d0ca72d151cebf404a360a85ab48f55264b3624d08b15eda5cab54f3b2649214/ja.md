```
lgl_sat(solver::LglPtr)::Cint
```

メインのSATルーチンを呼び出します。返り値は上記の通りです。例えば、`Lingeling.UNSATISFIABLE`、`Lingeling.SATISFIABLE`、または`Lingeling.UNKNOWN`です。

# 引数

  * `solver::LglPtr`: Lingeling SAT-Solverへのポインタ。

# 戻り値

  * `val::Cint`: SATルーチンの結果。(例: `Lingeling.UNSATISFIABLE`、

`Lingeling.SATISFIABLE`、または`Lingeling.UNKNOWN`)
