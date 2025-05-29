```
localfilter!(dst, A, B, filter!; order=FORWARD_FILTER) -> dst
```

は、ソース `A` をカーネル `B` でフィルタリングした結果で `dst` を上書きします。`order` による順序付けと、次のように呼び出される関数 `filter!` を使用します：

```
filter!(dst, A, order, ker, i, J)
```

ここで、`dst` の各インデックス `i` に対して、`J` は `i` の局所近傍のインデックスのサブセットです。そして、

```
ker = kernel(Dims{ndims(A)}, B)
```

はフィルタカーネルを表す配列です。関数 `filter!` は、局所フィルタリング操作の結果を計算し、位置 `i` の `dst` に格納します。

  * `order = FORWARD_FILTER` の場合、`J` は `A[j]` と `B[j-i]` が範囲内であるすべてのインデックス `j` のサブセットです。これは離散相関を実装するための自然な順序付けです。
  * `order = REVERSE_FILTER` の場合、`J` は `A[j]` と `B[i-j]` が範囲内であるすべてのインデックス `j` のサブセットです。これは離散畳み込みを実装するための自然な順序付けです。

順序に依存しないようにするために、`filter!` のコード内で `B[order(i,j)]` を使用して、`order` が `FORWARD_FILTER` か `REVERSE_FILTER` に応じて自動的に `B[j-i]` または `B[i-j]` を生成します。
