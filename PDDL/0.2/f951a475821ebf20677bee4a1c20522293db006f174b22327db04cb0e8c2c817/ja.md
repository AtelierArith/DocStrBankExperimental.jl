```
ground(domain::Domain, state::State, action::Action, args)
```

リフトされた `action` とアクション `args` に基づいて、グラウンドアクションを返します。もしアクションが `domain` と `state` に対して決して満たされない場合は、`nothing` を返します。
