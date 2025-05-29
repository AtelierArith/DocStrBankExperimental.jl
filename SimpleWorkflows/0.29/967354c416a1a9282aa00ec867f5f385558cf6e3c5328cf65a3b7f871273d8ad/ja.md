```
isfailed(wf::AbstractWorkflow)
```

`AbstractWorkflow`内のいずれかのジョブが失敗したかどうかを確認します。すべてのジョブが終了したことを前提とします。

すべてのジョブが終了した後にいずれかのジョブが失敗した場合は`true`を返し、そうでなければ`false`を返します。
