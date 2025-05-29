```
set_scheduler_max_job(max_done::Int = 10000, max_cancelled::Int = max_done)
```

完了したジョブの数を設定します。ジョブの数が 1.5*NUMBER を超えると、古いジョブが削除されます。
