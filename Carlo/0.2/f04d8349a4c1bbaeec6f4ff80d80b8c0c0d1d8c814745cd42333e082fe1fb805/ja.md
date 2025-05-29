```
start(job::JobInfo, ARGS)
```

ジョブスクリプトからこれを呼び出して、Carloコマンドラインインターフェースを開始します。

何らかの理由でジョブスクリプトを使用したくない場合は、次のようにして直接ジョブをスケジュールできます。

```
start(Carlo.MPIScheduler, job)
```
