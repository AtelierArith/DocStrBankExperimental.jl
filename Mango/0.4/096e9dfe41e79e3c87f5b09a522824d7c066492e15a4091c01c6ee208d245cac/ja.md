```
step_iteration(task_sim::TaskSimulation, step_size_s::Real)::TaskIterationResult
```

シミュレーションのステップのためのイテレーションを実行します。このとき、時間は `step_size_s` でステップされます。

他のタスクの結果や到着したメッセージの結果として新しいタスクが生成される場合、繰り返し呼び出すことができます。
