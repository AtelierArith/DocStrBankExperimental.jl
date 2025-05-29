```
OutputCollector(cmd::AbstractCmd; verbose::Bool = false)
```

Run `cmd`, and collect the output such that `stdout` and `stderr` are captured independently, but with the time of each line recorded such that they can be stored/analyzed independently, but replayed synchronously.
