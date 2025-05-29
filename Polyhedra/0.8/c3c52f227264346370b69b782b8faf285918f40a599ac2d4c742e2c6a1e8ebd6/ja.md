```
isredundant(p::Rep, idx::Index; strongly=false)
```

インデックス `idx` を持つ要素が `p` によって表される多面体を変更することなく削除できるかどうかを示す `Bool` を返します。`strongly` が `true` の場合、

  * `idx` が H-表現要素 `h` の場合、`h` のハイパープレーンに `p` の V-表現要素が存在しない場合にのみ `true` を返します。
  * `idx` が V-表現要素 `v` の場合、`v` が `p` の相対内部にある場合にのみ `true` を返します。
