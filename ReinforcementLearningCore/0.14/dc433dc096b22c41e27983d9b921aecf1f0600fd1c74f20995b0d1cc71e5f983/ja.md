```
ActorCritic(;actor, critic, optimizer=Adam())
```

`actor` 部分はロジットを返す必要があります (*最終層でソフトマックスを使用しないでください!*)、`critic` 部分は状態価値を返す必要があります。
