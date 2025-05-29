```
get_row(spmexp::SparseMatrixExp{N}, i::Int;
        [backend]=get_exponential_backend()) where {N}
```

スパース行列指数の単一行を返します。

### 入力

  * `spmexp`  – スパース行列指数
  * `i`       – 行インデックス
  * `backend` – （オプション; デフォルト: `get_exponential_backend()`）指数化バックエンド

### 出力

行列指数の `i` 番目の行に対応する行ベクトル。

### 注意事項

この実装は、結果を作成するためにJuliaの `transpose` 関数を使用します。結果は `Transpose` 型です; Juliaのバージョンがv0.7より古い場合、結果は `RowVector` 型でした。
