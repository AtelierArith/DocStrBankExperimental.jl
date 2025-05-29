```
CrosshairOptions(; kw...)
```

クロスヘアオプションを説明する構造体。

## キーワード引数

| 名前::型                             | デフォルト (可能な値)             | 説明        |
|:--------------------------------- |:------------------------ |:--------- |
| `mode::LWC_CROSSHAIR_MODE`        | `LWC_CROSSHAIR_MAGNET`   | クロスヘアモード。 |
| `vert_line::CrosshairLineOptions` | `CrosshairLineOptions()` | 垂直線オプション。 |
| `horz_line::CrosshairLineOptions` | `CrosshairLineOptions()` | 水平線オプション。 |
