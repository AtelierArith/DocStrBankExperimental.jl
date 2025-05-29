```
register!(s, what, Δ)
```

`what`を`s.now+Δ`の時刻に`s.event_queue`に置きます。`what`は`Scheduler`型の引数を正確に1つ受け入れなければなりません。この関数は`Δ`が有効（有限）な数であるかどうかをチェックしません。挿入された`Action`を返します。
