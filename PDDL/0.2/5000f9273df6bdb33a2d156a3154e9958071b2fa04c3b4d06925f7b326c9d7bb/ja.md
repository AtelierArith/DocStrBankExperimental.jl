```
execute!(domain::Domain, state::State, action::Action, args)
execute!(domain::Domain, state::State, action::Term)
```

`state`をインプレースで変更する[`execute`](@ref)のバリアントです。
