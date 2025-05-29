```
tohrep(P::LazySet)
```

多面体集合を制約表現に変換します。

### 入力

  * `P` – 多面体集合

### 出力

`P` が有界であれば `HPolyhedron`（`isboundedtype`を介して）、そうでなければ `HPolytope` を返します。
