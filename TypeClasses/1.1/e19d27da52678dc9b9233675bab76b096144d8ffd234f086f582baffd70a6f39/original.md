```
orelse(task1, task2, ...)
task1 ⊘ task2
```

Runs both in parallel and collects which ever result is first. Then interrupts all other tasks and returns the found result.
