```
struct AttractivenessMetaPOI <: AbstractMetaPOI
```

魅力のメタデータのコンテナ（スクレイピングのデフォルト設定）。

魅力は以下のフィールドによって定義されます：

  * `group` - POIのグループ（例： `:parking` または `:food`）
  * `influence` - 場所の魅力に対するPOIの影響力
  * `range` - POIの影響範囲（メートル単位で測定）
