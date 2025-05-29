```
SimpleSymmetry(map::T, dict::D) where {T,D}
```

`SimpleSymmetry{keytype(D),T,D}` オブジェクト `symm` を作成します。ここで `symm[x]` は次のようになります。

  * `x` が `keytype(D)` の場合、`map[dict[x]]`。
  * それ以外の場合、`x` が `Integer` の場合、`map[x]`。
