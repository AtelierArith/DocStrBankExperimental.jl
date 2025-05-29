```
ResultTypes.iserror(x) -> Bool
```

If `x` is an `Exception`, return `true`. If `x` is an `ErrorResult` (a `Result` containing an `Exception`), return `true`. Return `false` in all other cases.
