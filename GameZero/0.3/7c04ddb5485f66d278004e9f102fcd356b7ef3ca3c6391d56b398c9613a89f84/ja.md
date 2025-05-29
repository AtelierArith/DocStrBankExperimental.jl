```
schedule_interval(f::Function, interval, first_interval=interval)
```

関数ハンドルと秒単位の時間を受け取り、その間隔の後に関数を実行するように設定します。オプションの第3引数first_intervalを渡すことで、最初の実行の前にその時間だけ待機することができます。
