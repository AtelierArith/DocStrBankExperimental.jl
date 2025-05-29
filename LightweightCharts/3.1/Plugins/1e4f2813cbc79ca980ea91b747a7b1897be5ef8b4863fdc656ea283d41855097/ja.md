```
lwc_trend_line(start_index, start_price, end_index, end_price; kw...) -> LWCPlugin
```

`start_index` と `start_price` から始まり、`end_index` と `end_price` で終わるトレンドラインをチャートに追加します。

## キーワード引数

| 名前::型                            | デフォルト (可能な値)                  | 説明         |
|:-------------------------------- |:----------------------------- |:---------- |
| `line_color::String`             | ランダムカラー                       | ラインの色。     |
| `width::Int64`                   | `6`                           | ラインの幅。     |
| `show_labels::Bool`              | `true`                        | ラベルの可視性。   |
| `label_background_color::String` | `"rgba(255, 255, 255, 0.85)"` | ラベルの背景色。   |
| `label_text_color::String`       | `"rgb(0, 0, 0)"`              | ラベルのテキスト色。 |
