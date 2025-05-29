```
JobOfTask{S, T}(task::T, release::S, deadline::S, cost::S, priority::S, exec::Vector{ExecInterval{S}}
```

A real-time job of the given `task` with the given parameters, executing over the intervals in `exec`.
