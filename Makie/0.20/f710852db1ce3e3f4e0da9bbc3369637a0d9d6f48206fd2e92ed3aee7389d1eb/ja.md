```
register_interaction!(parent, name::Symbol, interaction)
```

`interaction`を`parent`に`name`という名前で登録します。親は、適切なイベントが発生するたびに`process_interaction(interaction, event, parent)`を呼び出します。

`deregister_interaction!`を使用してインタラクションを削除するか、`activate_interaction!` / `deactivate_interaction!`を使用して一時的に切り替えることができます。
