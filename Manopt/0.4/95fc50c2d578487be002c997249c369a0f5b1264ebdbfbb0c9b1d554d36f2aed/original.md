```
RecordEvery <: RecordAction
```

record only every $i$th iteration. Otherwise (optionally, but activated by default) just update internal tracking values.

This method does not perform any record itself but relies on it's children's methods
