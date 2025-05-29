```
regress(domain::Domain, state::State, action::Action, args)
regress(domain::Domain, state::State, action::Term)
```

`state`に関して`args`でパラメータ化された`action`の前像を計算します。アクションパラメータは、複合`Term`の引数としても指定できます。
