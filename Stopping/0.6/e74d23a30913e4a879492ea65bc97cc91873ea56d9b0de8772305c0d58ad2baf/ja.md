```
`update!(:: AbstractState; convert = false, kwargs...)`
```

状態のための汎用更新関数。この関数は、kwargsと状態のエントリを比較します。kwargsの型がエントリと同じであれば、更新されます。

kargs `convert` をtrueに設定すると、互換性のない型でも更新されます。

例: `update!(state1)` `update!(state1, current_time = 2.0)` `update!(state1, convert = true, current_time = 2.0)`

関連情報: `GenericState`, `reinit!`, `update_and_start!`, `update_and_stop!`
