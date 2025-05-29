```
alarm(hours, minutes, seconds;
    action = () -> @info("TickTock: time's up"))
```

アラームを設定し、アラームが鳴ったときに実行される匿名関数を提供するオプションがあります。

!!! warning
    ターミナルが占有されないように @async を使用してください！


```
@async alarm(0, 5, 0, action = ()-> println("TickTock.jl: 5 分が経過しました！"))

@async alarm(0, 0, 5, action = () -> run(`say "あなたのアールグレイが準備できました; サー"`), alarmname="お茶の時間です") # macOSのスピーチを使用
```
