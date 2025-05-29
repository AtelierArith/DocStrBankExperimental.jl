```julia
aggregator(f)

```

Wrap a function so that it maps columns of a `FunctionalTable` to a table with a single row, columwise, ignoring the index. Returns a closure.

# Example

```julia
map(aggregator(mean), by(ft, :col))
```

will calculate means after grouping by `:col`.
