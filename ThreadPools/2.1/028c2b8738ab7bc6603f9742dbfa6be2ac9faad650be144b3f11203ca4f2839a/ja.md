```
Base.put!(pool::LoggedQueuePool, fn, args...)
Base.put!(fn, pool::LoggedQueuePool, args...)
```

`fn(args...)`を実行し、それをプールに追加するタスクを作成し、プールに利用可能なスレッドができるまでブロックします。
