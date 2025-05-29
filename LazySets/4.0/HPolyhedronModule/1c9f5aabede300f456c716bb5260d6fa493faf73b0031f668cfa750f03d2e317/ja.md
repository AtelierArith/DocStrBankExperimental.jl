```
convex_hull(P1::HPoly, P2::HPoly;
           [backend]=default_polyhedra_backend(P1))
```

2つの多面体の制約表現における集合の和の凸包を計算します。

### 入力

  * `P1`      – 多面体
  * `P2`      – 多面体
  * `backend` – （オプション、デフォルト: `default_polyhedra_backend(P1)`）多面体計算のためのバックエンド

### 出力

`P1`と`P2`の具体的な凸包から得られる`HPolyhedron`（または`HPolytope`）。

### 注意事項

パフォーマンスの理由から、`convex_hull`には`CDDLib.Library()`バックエンドを使用することをお勧めします。

サポートされているバックエンドに関する詳細は[Polyhedraのドキュメント](https://juliapolyhedra.github.io/)を参照してください。
