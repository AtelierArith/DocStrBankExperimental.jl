```
function change_value(widget::WidgetProgressBar, new_value::Integer; color::Int = -1)
```

プログレスバーの値を `new_value` に変更します。

色はキーワード `color` で選択できます。負の値であれば（**デフォルト**）、現在の色は変更されません。
