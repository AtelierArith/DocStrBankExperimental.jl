```
SArray{S, T, N, L}(x::NTuple{L})
SArray{S, T, N, L}(x1, x2, x3, ...)
```

静的サイズの配列 `SArray` を構築します。この型は不変であるため、データは構築時に提供されなければならず、後で変更することはできません。`S` パラメータは配列の次元またはサイズを指定するタプル型であり、例えば 3×4×5 サイズの配列の場合は `Tuple{3,4,5}` となります。`N` パラメータは配列の次元であり、`L` パラメータは配列の `length` で、常に `prod(S)` に等しくなります。コンストラクタは、入力から推測可能な場合、`L`、`N`、および `T` パラメータを省略することができます（例えば、`L` は常に `S` から推測可能です）。

```
SArray{S}(a::Array)
```

配列 `a` からのデータを使用して、次元 `S`（`Tuple{...}` として表現）を持つ静的サイズの配列を構築します。`S` パラメータは必須であり、`a` のサイズはコンパイラには不明であるためです（要素型もオプションで指定できます）。
