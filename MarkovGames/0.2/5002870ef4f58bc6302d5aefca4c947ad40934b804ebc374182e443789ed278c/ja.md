```
isterminal(m::Game, s)
```

状態`s`が終端であるかどうかを確認します。状態が終端である場合、その状態ではアクションが行われず、追加の報酬も蓄積されません。したがって、そのような状態における価値関数は、定義上、ゼロです。
