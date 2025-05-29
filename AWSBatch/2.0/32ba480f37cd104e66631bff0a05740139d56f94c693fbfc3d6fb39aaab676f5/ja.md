```
BatchJob
```

バッチジョブIDを保存して、以下のことを行います：

  * ジョブとそのパラメータを`describe`する
  * ジョブの`status`を確認する
  * ジョブが完了するのを`wait`する
  * `log_events`を取得する

# フィールド

  * `id::AbstractString`: jobId
