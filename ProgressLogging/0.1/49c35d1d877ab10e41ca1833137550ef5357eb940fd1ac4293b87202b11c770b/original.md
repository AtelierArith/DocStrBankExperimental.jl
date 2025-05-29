```
@logprogress [name] progress [key1=val1 [key2=val2 ...]]
```

This macro must be used inside [`@withprogress`](@ref) macro.

Log a progress event with a value `progress`.  The expression `progress` must be evaluated to be a real number between `0` and `1` (inclusive), a `NaN`, or a string `"done"`.

Optional first argument `name` can be used to change the name of the progress bar.  Additional keyword arguments are passed to `@logmsg`.
