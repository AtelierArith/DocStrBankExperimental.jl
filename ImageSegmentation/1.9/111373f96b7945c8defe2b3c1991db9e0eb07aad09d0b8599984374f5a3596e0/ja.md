```
mask = flood(src, idx, nbrhood_function=diamond_iterator((3,3,...)); thresh)
```

配列 `mask` を返します。これは `src` と同じ軸を持ち、`src[i]` が `src[idx]` からのユークリッド距離が `thresh` 未満であるすべての接続された要素に対して `true` にマークされています。
