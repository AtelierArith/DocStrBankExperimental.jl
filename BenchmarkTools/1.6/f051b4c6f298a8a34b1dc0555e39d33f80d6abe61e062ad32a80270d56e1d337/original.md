```
isempty(group::BenchmarkGroup)
```

Return `true` if `group` is empty. This will first run `clear_empty!` on `group` to recursively remove any empty subgroups.
