```
relevant(domain::Domain, state::State, action::Action, args)
relevant(domain::Domain, state::State, action::Term)
```

`args`によってパラメータ化された`action`が、指定された`domain`内の`state`に関連しているか（導くことができるか）を確認します。アクションのパラメータは、複合`Term`の引数としても指定できます。
