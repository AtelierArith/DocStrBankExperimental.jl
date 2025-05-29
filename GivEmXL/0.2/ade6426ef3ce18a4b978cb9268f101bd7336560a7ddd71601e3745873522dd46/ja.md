```
write_errors(errf, errors) → errored::Bool
```

エラーのバックトレースをファイルに保存します。

# 引数

  * `errf`: エラーが保存されるファイル。
  * `errors`: バックトレースの配列

# 戻り値

  * `errored`: `errors` が空の配列の場合は `false`。

関数 `write_errors` は公開されており、エクスポートされていません。
