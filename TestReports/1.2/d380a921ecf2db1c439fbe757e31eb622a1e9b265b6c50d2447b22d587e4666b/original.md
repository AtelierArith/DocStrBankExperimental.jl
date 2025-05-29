```
any_problems(ts)
```

Checks a testset to see if there were any problems (`Error`s or `Fail`s). Note that unlike the `DefaultTestSet`, the `ReportingTestSet` does not throw an exception on a failure. Thus to set the exit code from the runner code, we check it using `exit(any_problems(top_level_testset))`.
