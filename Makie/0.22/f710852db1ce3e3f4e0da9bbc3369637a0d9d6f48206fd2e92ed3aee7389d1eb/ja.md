```
register_interaction!(parent, name::Symbol, interaction)
```

`interaction`を`parent`に`name`の名前で登録します。親は、適切なイベントが発生するたびに`process_interaction(interaction, event, parent)`を呼び出します。

`interaction`は`deregister_interaction!`で削除することができ、`activate_interaction!` / `deactivate_interaction!`で一時的に切り替えることができます。
