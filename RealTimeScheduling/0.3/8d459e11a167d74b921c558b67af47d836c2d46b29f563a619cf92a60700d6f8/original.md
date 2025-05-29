```
ExecInterval{S}(start::S, stop::S, proc::Int)
```

Interval type for job execution, with a specified processor index.  Always assumed to be half open, i.e., `[start, stop)`.
