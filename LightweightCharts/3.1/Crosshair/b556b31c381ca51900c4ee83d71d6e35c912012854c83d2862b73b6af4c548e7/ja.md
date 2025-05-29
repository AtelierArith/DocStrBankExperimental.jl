```
CrosshairLineOptions(; kw...)
```

クロスヘアライン（垂直または水平）を説明する構造体。

## キーワード引数

| 名前::型                             | デフォルト（可能な値）                  | 説明                      |
|:--------------------------------- |:---------------------------- |:----------------------- |
| `color::String`                   | `'#758696'`                  | クロスヘアラインの色。             |
| `width::Int64`                    | `1`                          | クロスヘアラインの幅。             |
| `style::LWC_CROSSHAIR_LINE_STYLE` | `LWC_CROSSHAIR_LARGE_DASHED` | クロスヘアラインのスタイル。          |
| `visible::Bool`                   | `true`                       | クロスヘアラインを表示する。          |
| `label_visible::Bool`             | `true`                       | 関連するスケールにクロスヘアラベルを表示する。 |
| `label_background_color::String`  | `'#4c525e'`                  | クロスヘアラベルの背景色。           |
