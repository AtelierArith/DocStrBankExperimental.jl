```
function process_focus(widget, k::Keystroke)
```

ウィジェット `widget` がフォーカスされているときにアクションを処理し、キー入力 `k` が押されたときに実行されます。`false` を返す場合は、ウィジェットがフォーカスを処理できなかったことを意味します。それ以外の場合は、`true` を返さなければなりません。
