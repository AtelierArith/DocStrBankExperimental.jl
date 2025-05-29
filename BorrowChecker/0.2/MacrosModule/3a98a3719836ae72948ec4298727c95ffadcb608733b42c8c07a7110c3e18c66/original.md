```
@move [:mut] new = old
```

Transfer ownership from one variable to another, invalidating the old variable. If `:mut` is specified, the destination will be mutable. Otherwise, the destination will be immutable. For `isbits` types, this will automatically use `@clone` instead.
