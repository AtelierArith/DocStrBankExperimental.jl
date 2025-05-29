```
TryCatch(stat; error_limit=1000, error_message_limit=90)
```

Wrap each call to `fit!` in a `try`-`catch` block and track the errors encountered (via [`CountMap`](@ref)).   Only `error_limit` unique errors will be included in the `CountMap`.  If a new error occurs after  `error_limit` has been reached, it will be included in the `CountMap` as `"Other"`.  Only the first  `error_message_limit` characters of each error message will be recorded.

# Example

```
o = TryCatch(Mean())

fit!(o, [1, missing, 3])

OnlineStatsBase.errors(o)
```
