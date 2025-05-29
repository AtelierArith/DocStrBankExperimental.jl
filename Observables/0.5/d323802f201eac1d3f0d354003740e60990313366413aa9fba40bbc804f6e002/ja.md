```
throttle(dt, input::AbstractObservable)
```

信号を制御して、最大で `dt` 秒ごとに1回だけ更新します。制御された信号は、各 `dt` 秒の時間ウィンドウ内で `input` 信号の最後の更新を保持します。
