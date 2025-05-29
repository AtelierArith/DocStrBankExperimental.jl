```
CompnentError{I,E} <: Exception
```

コンポーネントで発生したエラーを保存し、追加の `index` が保存されます。

# フィールド

  * `index::I` エラーが発生したインデックス
  * `error::E` 発生したエラー。
