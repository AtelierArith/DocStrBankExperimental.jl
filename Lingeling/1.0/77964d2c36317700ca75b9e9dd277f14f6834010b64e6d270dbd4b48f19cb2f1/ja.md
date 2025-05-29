```
lgl_reuse(solver::LglPtr, lit::Integer)
```

リテラルを再利用可能にします。リテラルが最後の `lgl_sat` の呼び出し中に凍結されていなかったが再利用可能な場合、この関数を使用して再び使用可能にすることができます。

# 引数

  * `solver::LglPtr`: Lingeling SAT-Solver へのポインタ。
  * `lit::Integer`: 再利用可能にするリテラル。

# 例外

  * `InexactError`: リテラルを `Cint` に変換できない場合。
