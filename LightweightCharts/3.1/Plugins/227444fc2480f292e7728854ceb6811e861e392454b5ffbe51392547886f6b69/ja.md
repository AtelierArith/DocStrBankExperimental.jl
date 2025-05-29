```
lwc_vert_line(index::Int64; kw...) -> LWCPlugin
```

`index`に基づいてチャートに垂直線を追加します。

## キーワード引数

| 名前::型                            | デフォルト (可能な値) | 説明         |
|:-------------------------------- |:------------ |:---------- |
| `label_text::String`             | `""`         | 垂直線のラベル。   |
| `width::Float64`                 | `3.0`        | 垂直線の幅。     |
| `color::String`                  | ランダムな色       | 垂直線の色。     |
| `label_background_color::String` | ランダムな色       | ラベルの背景色。   |
| `label_text_color::String`       | `"white"`    | ラベルのテキスト色。 |
| `show_label::Bool`               | `false`      | ラベルの表示可否。  |
