```
register_interaction!(interaction::Function, parent, name::Symbol)
```

`interaction`を`parent`に`name`の名前で登録します。親は、適切なイベントが発生するたびに`process_interaction(interaction, event, parent)`を呼び出します。この最初の`Function`引数を持つ形式は、特に`do`構文のために意図されています。

`deregister_interaction!`を使用してインタラクションを削除するか、`activate_interaction!` / `deactivate_interaction!`を使用して一時的に切り替えることができます。
