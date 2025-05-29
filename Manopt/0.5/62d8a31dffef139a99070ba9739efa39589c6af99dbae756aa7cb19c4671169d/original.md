```
RecordEvery <: RecordAction
```

record only every $k$th iteration. Otherwise (optionally, but activated by default) just update internal tracking values.

This method does not perform any record itself but relies on it's children's methods
