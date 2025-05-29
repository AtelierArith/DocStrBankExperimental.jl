```
lgl_deref(solver::LglPtr, lit::Integer)::Cint
```

'lgl_sat' が呼び出され、`Lingeling.SATISFIABLE` を返した後、満足する割り当てはリテラルを「逆参照」することで取得できます。リテラルの値は、真の場合は `1`、偽の場合は `-1`、不明な値の場合は `0` として返されます。

# 引数

  * `solver::LglPtr`: Lingeling SAT-Solver へのポインタ。
  * `lit::Integer`: 逆参照するリテラル。

# 戻り値

  * `val::Cint`: リテラルの値。真の場合は `1`、偽の場合は `-1`、不明な場合は `0`。

# 例外

  * `InexactError`: リテラルを `Cint` に変換できない場合。
