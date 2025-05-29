```
repeat_register!(s, what, interval)
```

`what`を`s.event_queue`に、`interval`関数で指定された時間間隔で繰り返し追加します。`interval`関数は、`Scheduler`型の引数を1つ受け取る必要があります。`what`は、`Scheduler`型の引数を正確に1つ受け取る必要があります。`interval`関数は、前のイベントが実行された後に呼び出されます。戻り値は`nothing`です。`interval`内で`terminate!`を呼び出してもシミュレーションは停止しません。代わりに、`interval`が`nothing`を返すと、アクションはスケジュールされず、`repeat_register`は実質的に終了します。
