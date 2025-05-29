```
lwc_vert_line(; kw...) -> LWCPlugin
```

カーソルに従って値を表示する動的ツールチップをチャートに追加します。

## キーワード引数

| 名前::型                              | デフォルト (可能な値)                            | 説明              |
|:---------------------------------- |:--------------------------------------- |:--------------- |
| `line_color::String`               | `"rgba(0, 0, 0, 0.2)"`                  | ツールチップの線の色。     |
| `title::String`                    | `""`                                    | ツールチップのタイトル。    |
| `follow_mode::LWC_TOOLTIP_TYPE`    | `LWC_TOOLTIP_TOP` (`LWC_TOOLTIP_TRACK`) | ツールチップの位置。      |
| `horizontal_deadzone_width::Int64` | `45`                                    |                 |
| `vertical_deadzone_height::Int64`  | `100`                                   | 水平デッドゾーンの高さ。    |
| `vertical_spacing::Int64`          | `20`                                    | 垂直間隔。           |
| `top_offset::Int64`                | `20`                                    | ツールチップの垂直オフセット。 |
