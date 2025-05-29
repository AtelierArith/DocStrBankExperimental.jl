```
chomsky_normal_form(tree, factor=RightFactored(), labelf)
```

木をチョムスキー標準形に変換します。

# 引数

  * `tree`: 変換する構成木
  * `factor=RightFactored()`: `LeftFactored()` または `RightFactored()` を指定できます
  * `labelf`: 関数（`labelf(tree, children)` のように呼び出されます）

# 戻り値

  * 引数と同じ型の木
