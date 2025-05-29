```
struct SourceReinjection{Dim}
```

特定の位置でデータを再注入します。

### フィールド

  * `points`: `[p1, p2, ...]` の形式のベクターで、`pi` は `(x)` または `(x, y)` のような点です。データは、`points` のメンバーが少なくとも1つ含まれるすべてのビンに均等に再注入されます。
  * `fallback`: ビンにポイントが含まれていない場合や再注入するデータがない場合に適用する `ReinjectionAlgorithm`。

### コンストラクタ

```
SourceReinjection(points; fallback = DataReinjection())
```
