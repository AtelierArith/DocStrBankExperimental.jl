```
merge(collector::OutputCollector; colored::Bool = false)
```

Merge the stdout and stderr streams of the [`OutputCollector`](@ref) on a per-line basis, returning a single string containing all collected lines, interleaved by capture time.  If `colored` is set to true, embeds terminal color codes to print `stderr` in red.
