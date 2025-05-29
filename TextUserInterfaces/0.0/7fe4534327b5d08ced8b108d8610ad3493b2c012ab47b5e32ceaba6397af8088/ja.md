```
function create_widget(T, parent::Window, begin_y::Integer, begin_x::Integer, vargs...; kwargs...)
```

ウィジェットのタイプ `T` を親ウィンドウ `parent` に作成します。ウィジェットは親ウィンドウの座標 `(begin_y, begin_x)` に配置されます。

各ウィジェットに関連する追加の変数とキーワードは、それぞれ `vargs` と `kwargs` を使用して渡すことができます。
