```
alarm(dt::DateTime;
    action = () -> @info("TickTock: time's up"))
```

指定した時刻 `dt` に発火するアラームを実行し、アラームが発火したときに実行される関数を提供するオプションがあります。

# 例

```
using Dates

dt = now() + Dates.Minute(1)

@async alarm(dt, action = () -> println("TickTock.jl: Ready!"))
```

```
@async alarm(now() + Dates.Minute(10) + Dates.Second(0), action = () -> run(`say "wake up, 10 minutes is up"`)) # macOS の音声コマンド
```
