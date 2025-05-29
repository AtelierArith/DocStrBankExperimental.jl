```
@maybe_inferred [Type] f(...)
```

`@inferred`と似ていますが、テストがPkgEvalの一部として実行される場合や、環境変数`CHAINRULES_TEST_INFERRED`が`false`に設定されている場合は、戻り値の型をチェックしません。
