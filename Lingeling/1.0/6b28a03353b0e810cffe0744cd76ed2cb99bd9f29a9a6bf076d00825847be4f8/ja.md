```
lgl_usable(solver::LglPtr, lit::Integer)::Cint
```

リテラルが使用可能かどうかを確認します。リテラルは、最後の `lgl_sat` の呼び出し中に凍結されなかった場合、使用不可能になります。使用不可能であることは、次の `lgl_add` の呼び出しでそのリテラルを使用することが許可されていないことを意味します。

# 引数

  * `solver::LglPtr`: Lingeling SAT-Solver へのポインタ。
  * `lit::Integer`: チェックするリテラル。

# 戻り値

  * `val::Cint`: リテラルが使用可能かどうか。使用可能であれば `1`、そうでなければ `0`。

# 例外

  * `InexactError`: リテラルを `Cint` に変換できない場合。
