```
state(j::LocalQuantumJob, ::Val{true})
state(j::LocalQuantumJob, ::Val{false})
state(j::LocalQuantumJob)
```

ジョブ `j` の状態を取得します。ローカルジョブは完了するまでブロックされ、`state` は常に `"COMPLETED"` です。
