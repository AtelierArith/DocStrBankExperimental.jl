```
isfailed(wf::AbstractWorkflow)
```

すべてのジョブが終了した場合に、`AbstractWorkflow`内のジョブが失敗したかどうかを確認します。

すべてのジョブが終了した後に、いずれかのジョブが失敗した場合は`true`を返し、そうでなければ`false`を返します。
