```
autotype(X; kw...)
```

`X`の各列に対する推奨されるscitypesの辞書を返します。これは、ルールに基づいたテーブルまたは配列です。

## Kwargs

  * `only_changes=true`:       trueの場合、autotypeを適用することが従来の慣習を使用することと異なる名前の辞書のみを返します。autotypeで強制する際は、`only_changes`をtrueにする必要があります。
  * `rules=(:few_to_finite,)`: 適用するルールのセットです。
