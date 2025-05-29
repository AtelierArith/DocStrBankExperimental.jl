```
nextstate!(b::FSMBehavior, state::FSMState)
```

FSMの次の状態を設定します。遷移は、状態のアクションメソッドから呼び出された場合、現在のアクションが完了した後に発生します。
