```
@proc [ret] function name() end
```

関数を `@code` ブロックに変換し、`IR.proc` を呼び出します。関数が再帰的な場合、戻り値の型 `ret` を指定する必要があります。
