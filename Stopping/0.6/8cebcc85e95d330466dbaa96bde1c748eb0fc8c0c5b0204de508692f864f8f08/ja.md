```
`reinit!(:: AbstractState, :: T; kwargs...)`

すべてのエントリを`_init_field`に設定する関数。ただし、必須の`x`は除く。

注意: `x`がkargsとして与えられた場合、第二引数よりも優先される。

例: `reinit!(state2, zeros(2))` `reinit!(state2, zeros(2), current_time = 1.0)`

状態内の`x`を再利用する短いバージョンの`reinit!`があります。

```

`reinit!(:: AbstractState; kwargs...)`

```

例: `reinit!(state2)` `reinit!(state2, current_time = 1.0)`
```
