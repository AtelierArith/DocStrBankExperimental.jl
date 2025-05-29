```
execute(domain::Domain, state::State, action::Action, args)
execute(domain::Domain, state::State, action::Term)
```

与えられた `state` で `args` によってパラメータ化された `action` を実行し、結果の状態を返します。アクションパラメータは、複合 `Term` の引数としても指定できます。
