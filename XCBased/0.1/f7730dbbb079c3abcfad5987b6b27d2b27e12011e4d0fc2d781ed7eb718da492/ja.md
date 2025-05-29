```
XCBVisualType
```

いくつかの画面のいくつかの深さに対して許可される視覚情報。[`XCBScreen`](@ref)を参照してください。構造体は以下のフィールドを持っています：

  * `visual_id` – 視覚タイプに対応するXID
  * `class` – `XCB_VISUAL_CLASS_STATIC_GRAY`、`XCB_VISUAL_CLASS_GRAY_SCALE`、`XCB_VISUAL_CLASS_STATIC_COLOR`、`XCB_VISUAL_CLASS_PSEUDO_COLOR`、`XCB_VISUAL_CLASS_TRUE_COLOR`、および`XCB_VISUAL_CLASS_DIRECT_COLOR`のいずれか
  * `bits_per_rgb_value` – 赤、緑、青のそれぞれの異なる色の強度値の数のlog2
  * `colormap_entries` – 新しく作成されたカラーマップ内の利用可能なカラーマップエントリの数
  * `red_mask` – `XCB_VISUAL_CLASS_DIRECT_COLOR`および`XCB_VISUAL_CLASS_TRUE_COLOR`のみに定義される
  * `green_mask` – `XCB_VISUAL_CLASS_DIRECT_COLOR`および`XCB_VISUAL_CLASS_TRUE_COLOR`のみに定義される
  * `blue_mask` – `XCB_VISUAL_CLASS_DIRECT_COLOR`および`XCB_VISUAL_CLASS_TRUE_COLOR`のみに定義される
