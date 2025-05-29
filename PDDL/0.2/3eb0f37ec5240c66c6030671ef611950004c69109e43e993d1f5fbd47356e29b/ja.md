```
available(domain::Domain, state::State, action::Action, args)
available(domain::Domain, state::State, action::Term)
```

指定された `state` と `domain` で `args` によってパラメータ化された `action` が実行可能かどうかを確認します。アクションパラメータは、複合 `Term` の引数としても指定できます。
