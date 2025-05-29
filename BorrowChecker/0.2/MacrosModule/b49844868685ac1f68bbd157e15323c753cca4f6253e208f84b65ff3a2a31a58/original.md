```
@clone [:mut] new = old
```

Create a deep copy of a value, without moving the source. If `:mut` is specified, the destination will be mutable. Otherwise, the destination will be immutable.
