```
JobOfTask{S, T}(task::T, release::S, deadline::S, cost::S, priority::S, exec::Vector{ExecInterval{S}}
```

与えられたパラメータを持つ指定された `task` のリアルタイムジョブで、`exec` の間隔で実行されます。
