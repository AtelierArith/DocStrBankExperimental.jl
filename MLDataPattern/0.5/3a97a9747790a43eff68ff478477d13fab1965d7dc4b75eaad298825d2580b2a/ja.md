```
getobs!(buffer, data, [idx], [obsdim]) -> buffer
```

`data` における指定されたインデックス `idx` に対応する観測値を `buffer` に書き込みます。`idx` は `Int` または `AbstractVector` 型であることに注意してください。

`data` に対して明示的に実装されていない限り、デフォルトでは `getobs(data, idx, obsdim)` を返し、その場合 `buffer` は無視されます。

`data` の型にとって意味がある場合、`obsdim` を使用して `data` のどの次元が観測値を示すかを指定できます。これは、位置引数として型安定な方法で指定することができます（`?LearnBase.ObsDim` を参照）、またはより便利にスマートキーワード引数として指定することができます。
