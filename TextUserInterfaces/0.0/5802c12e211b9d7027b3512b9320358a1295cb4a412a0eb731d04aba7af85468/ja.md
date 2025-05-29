```
function set_focus_chain(wins::Window...; new_focus_id::Integer = 1)
```

フォーカスチェーンを設定します。すなわち、フォーカスを受け取ることができるウィンドウの順序付きリストです。キーワード `new_focus_id` を設定することで、新しいチェーンの中で現在フォーカスされている要素を指定できます。
