```
repeat_bulk_register!(s, who, what, interval, randomize)
```

指定された時間間隔で `bulk_register!` を繰り返します。`interval` 関数は `Scheduler` 引数を受け入れる必要があります。`interval` 関数は前のイベントが実行された後に呼び出されます。`what` は `Scheduler` と `typeof(who)` の2つの引数を正確に受け入れる必要があります。戻り値は `nothing` です。`interval` 関数内で `terminate!` を呼び出してもシミュレーションは停止しません。代わりに、`interval` が `nothing` を返すと、アクションはスケジュールされず、`repeat_register` は実質的に終了します。
