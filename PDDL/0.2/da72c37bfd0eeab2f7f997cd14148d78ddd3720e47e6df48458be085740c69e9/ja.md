```
regress!(domain::Domain, state::State, action::Action, args)
regress!(domain::Domain, state::State, action::Term)
```

[`regress`](@ref) のバリアントで、`state` をインプレースで変更します。
