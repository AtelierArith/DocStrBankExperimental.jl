```
UpdateEveryN(n, update_signal_type, reset_signal_type = Nothing)
```

`UpdateSignalHandler`は、`needs_update!`が`update_signal_type`の`UpdateSignal`で呼び出されるたびに`n`回ごとに更新を行います。`reset_signal_type`が指定されている場合、カウンター（0から`n`までインクリメントされ、次の更新を行う時に0にリセットされる）は、信号ハンドラーが`reset_signal_type`の`UpdateSignal`で`needs_update!`されるたびに0にリセットされます。
