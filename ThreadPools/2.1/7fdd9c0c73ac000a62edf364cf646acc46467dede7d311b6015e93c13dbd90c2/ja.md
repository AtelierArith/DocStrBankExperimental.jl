```
Base.put!(pool::LoggedQueuePool, t::Task)
```

タスク`t`をプールに追加し、プールに利用可能なスレッドができるまでブロックします。
