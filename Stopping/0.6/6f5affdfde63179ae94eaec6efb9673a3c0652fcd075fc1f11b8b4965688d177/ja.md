```
`reinit!(:: AbstractStopping; rstate :: Bool = false, kwargs...)`
```

Stoppingのメタデータを再初期化します。

注意:

  * `rstate`が`true`に設定されている場合、現在の状態を再初期化します

(その際にkwargsを使用します)。

  * `rlist`がtrueに設定されている場合、状態のリストも再初期化されます。`rstate`が`true`の場合は`VoidListofStates`として、そうでない場合は現在の状態のみを含むリストとして設定されます。
