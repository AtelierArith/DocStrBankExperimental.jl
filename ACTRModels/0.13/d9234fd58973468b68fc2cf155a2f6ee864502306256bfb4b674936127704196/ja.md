```
match(chunk::AbstractChunk, funs...; request...)
```

リクエストがチャンクに一致するかどうかを示すブール値を返します。スロットがチャンクに存在しない場合や、スロットの値がリクエストの値と一致しない場合は、falseが返されます。

  * `chunk::AbstractChunk`: チャンクオブジェクト
  * `funs...`: `!=, ==`などの関数のリスト
  * `request...`: スロット値ペアのNamedTuple
