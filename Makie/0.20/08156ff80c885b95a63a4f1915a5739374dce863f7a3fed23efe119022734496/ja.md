```
register_interaction!(interaction::Function, parent, name::Symbol)
```

`interaction`を`parent`に`name`という名前で登録します。親は、適切なイベントが発生するたびに`process_interaction(interaction, event, parent)`を呼び出します。この最初の`Function`引数を持つ形式は、特に`do`構文のために意図されています。

`interaction`は`deregister_interaction!`で削除することができ、`activate_interaction!` / `deactivate_interaction!`で一時的に切り替えることができます。
