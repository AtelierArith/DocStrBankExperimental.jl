```
ITensor([ElT::Type, ]x::Number, inds)
ITensor([ElT::Type, ]x::Number, inds::Index...)
```

すべての要素が `x` に設定され、インデックス `inds` を持つ ITensor を構築します。

もし `x` が `Int` または `Complex{Int}` の場合、要素は `float(x)` に設定されますが、最初の入力で別途指定されていない限りです。

ストレージは `NDTensors.Dense` タイプになります。

# 例

```julia   i = Index(2,"index*i"); j = Index(4,"index*j"); k = Index(3,"index_k");

A = ITensor(1.0, i, j)   A = ITensor(1, i, j) # 上と同じ   B = ITensor(2.0+3.0im, j, k)   ```

!!! warning       将来のバージョンでは、整数入力を `float` に自動的に変換しない可能性があり、その場合は特定の要素タイプに依存しない方が良いでしょう。
