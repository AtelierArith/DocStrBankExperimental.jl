```
writeframe(io::CSeis, trcs, idx...)
```

Write a frame to `io`.  The location of the frame is determined from `idx...` which can either be integer(s) or a `CartesianIndex`.  A minimal set of headers are created from `idx...` and are also written to `io`.
