```
isrunning(job::Job)
isrunning(s::Server, jobdir::String)
```

ジョブが実行中かどうかを返します。ジョブが `slurm` を使用して送信された場合、`QUEUED` ステータスも実行中としてカウントされます。
