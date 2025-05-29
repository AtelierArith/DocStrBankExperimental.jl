```
onworker(
    f::Function, args...;
    pool::AbstractWorkerPool = ppt_worker_pool(),
    maxtime::Real = 0, tries::Integer = 1, label::AbstractString = ""
)
```

指定された `pool` から利用可能なワーカープロセスで `f(args...)` を実行し、結果を返します。

`maxtime > 0` の場合、アクティビティの最大時間が設定されます。アクティビティが `maxtime` 秒を超えて長くかかると、それを実行しているプロセス（メインプロセスでない場合）は終了します。

`label` はデバッグログに使用されます。

アクティビティの実行中に問題が発生した場合（maxtime またはワーカーの失敗）、最大試行回数に達していない場合はタスクを再スケジュールし、そうでない場合は例外をスローします。
