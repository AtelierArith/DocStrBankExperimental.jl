```
orelse(future1, future2, ...)
future1 ⊘ future2
```

Runs both in parallel and collects which ever result is first. Then interrupts all other futures and returns the found result.
