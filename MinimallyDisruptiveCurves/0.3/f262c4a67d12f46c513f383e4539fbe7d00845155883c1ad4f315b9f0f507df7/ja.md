```
(c::MDCProblem)()
```

は、MDCProblemによって指定されたODEProblemsのタプルを返します。通常は単一のODEProblemです。曲線がゼロを横切る場合は2つが提供され、ゼロから前後に進む2つの曲線を並行して実行できるようになります。
