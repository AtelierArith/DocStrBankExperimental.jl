```
function create_form(fields::Vector{TUI_FIELD}; ...)
```

フィールド `fields` を持つ新しいフォームを作成します。

# キーワード

  * `newline_overload`: `REQ_NEW_LINE` のオーバーロードを有効にします。                     (**デフォルト** = `false`)
  * `backspace_overload`: `REQ_DEL_PREV` のオーバーロードを有効にします。                       (**デフォルト** = `false`)
