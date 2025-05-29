```
tohrep(P::VPolygon, ::Type{HPOLYGON}=HPolygon) where {HPOLYGON<:AbstractHPolygon}
```

与えられたポリゴンの制約表現を構築します。

### 入力

  * `P`        – 頂点表現のポリゴン
  * `HPOLYGON` – （オプション、デフォルト: `HPolygon`）ターゲットポリゴンの型

### 出力

制約表現のポリゴン、`AbstractHPolygon`。

### アルゴリズム

アルゴリズムは、各連続する頂点のペアに対してエッジを追加します。頂点はすでに反時計回り（CCW）に順序付けられているため、制約は自動的にソートされます（CCW）。
