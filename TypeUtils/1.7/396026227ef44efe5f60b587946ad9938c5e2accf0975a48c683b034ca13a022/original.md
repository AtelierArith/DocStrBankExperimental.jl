```
TypeUtils.@public args...
```

declares `args...` as being `public` even though they are not exported. For Julia version < 1.11, this macro does nothing. Using this macro also avoid errors with CI and coverage tools.
