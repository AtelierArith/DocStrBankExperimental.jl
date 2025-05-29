```
readframetrcs!(io::CSeis, trcs, idx...[; regularize=true])
```

Read traces from `io` into `trcs::Matrix` for the frame `idx...`. `idx...` can either be integer(s) or a `CartesianIndex`.

The `regularize` named argument is only applicable when the compression method is `LeftJustifyCompressor`.  If set to true, then traces are  regularized to their correct context locations.  Otherwise, they remain left justified.  Note that one can subsequently use the `regularize!` method.
