```
function change_text(widget::WidgetLabel, new_text::AbstractString; alignment = :l, color::Int = -1)
```

ラベルウィジェット `widget` のテキストを `new_text` に変更します。

ウィジェット内のテキストの配置は、キーワード `alignment` によって選択できます。選択肢は次の通りです：

  * `:l`: 左揃え (**デフォルト**);
  * `:c`: 中央揃え; または
  * `:r`: 右揃え。

テキストの色は、キーワード `color` によって選択できます。負の値であれば (**デフォルト**)、現在の色は変更されません。
