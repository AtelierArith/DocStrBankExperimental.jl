```
@runstate eff
```

Callableとは異なり、Stateは常に最初の外側のEffとして実行されることを保証する必要があります。これは、内部の状態を追加の引数として返すためです。

例えば、`@runstate @runcallable eff`のようにruncallableでネストすると、追加された状態がCallable内にあり、State内には直接ないため、機能しません。
