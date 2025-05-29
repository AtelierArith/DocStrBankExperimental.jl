```
clear_empty!(group::BenchmarkGroup)
```

Recursively remove any empty subgroups from `group`.

Use this to prune a `BenchmarkGroup` after accessing the incorrect fields, such as `g=BenchmarkGroup(); g[1]`, without storing anything to `g[1]`, which will create an empty subgroup `g[1]`.
