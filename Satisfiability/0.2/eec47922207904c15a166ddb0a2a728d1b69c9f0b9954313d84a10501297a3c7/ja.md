```
reset_assertions!(solver::InteractiveSolver)
```

すべてのアサーションを削除し、ソルバーのアサーションスタックからnレベルをポップします。このコマンドの後、スタックはレベル1になり、設定されたアサーションはありません。SMT-LIB標準の[セクション4.2.1](http://smtlib.cs.uiowa.edu/papers/smt-lib-reference-v2.6-r2021-05-12.pdf)を参照してください。
