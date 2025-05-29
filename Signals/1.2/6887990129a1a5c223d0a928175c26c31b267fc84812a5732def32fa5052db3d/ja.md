```
s = fpswhen(switch::Signal, freq; duration = Inf)
```

`switch` の値が `true` の場合に限り、`duration` 秒間、現在のタイムスタンプに対して `freq` 回/秒 更新される信号です。
