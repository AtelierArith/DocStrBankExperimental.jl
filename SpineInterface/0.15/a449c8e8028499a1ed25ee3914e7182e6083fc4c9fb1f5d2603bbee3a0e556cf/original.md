```
collect_indexed_values(d)
```

A parsed value (TimeSeries, TimePattern, Map, etc.) from a Dict mapping indexes to values.

## Examples

```
@assert collect_indexed_values(indexed_values(ts)) == ts
```
