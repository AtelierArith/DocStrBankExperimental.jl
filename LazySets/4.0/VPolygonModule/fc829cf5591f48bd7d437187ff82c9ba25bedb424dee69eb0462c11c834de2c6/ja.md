# 拡張ヘルプ

```
intersection(P1::VPolygon, P2::VPolygon; apply_convex_hull::Bool=true)
```

### 出力

`VPolygon`、または交差が空の場合は`EmptySet`。

### アルゴリズム

この関数は、[サザーランド–ホッジマン多角形クリッピングアルゴリズム](https://en.wikipedia.org/wiki/Sutherland%E2%80%93Hodgman_algorithm)を適用します。実装は[ロゼッタコード](http://www.rosettacode.org/wiki/Sutherland-Hodgman_polygon_clipping#Julia)に見られるものに基づいています。
