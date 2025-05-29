```
lgl_reusable(solver::LglPtr, lit::Integer)::Cint
```

リテラルが再利用可能かどうかを確認します。リテラルは、最後の `lgl_sat` の呼び出し中に凍結されていない可能性がありますが、それでも再利用可能である可能性があります（したがって、`lgl_reuse` を使用して再度使用可能にすることができます）。

# 引数

  * `solver::LglPtr`: Lingeling SAT-Solver へのポインタ。
  * `lit::Integer`: チェックするリテラル。

# 戻り値

  * `val::Cint`: リテラルが再利用可能かどうか。再利用可能であれば `1`、そうでなければ `0`。

# 例外

  * `InexactError`: リテラルを `Cint` に変換できない場合。
