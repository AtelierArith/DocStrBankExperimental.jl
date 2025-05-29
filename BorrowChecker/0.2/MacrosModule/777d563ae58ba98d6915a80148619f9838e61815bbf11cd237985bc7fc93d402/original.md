```
@take! var
```

Take ownership of a value, typically used in function arguments. Returns the inner value and marks the original as moved. For `isbits` types, this will return a copy and not mark the original as moved.
