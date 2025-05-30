```
WithIOContext(x, properties::Pair...)
```

A wrapper around `x` with extra IOContext properties set, just for the display of `x`.

# Examples

```julia
WithIOContext(rand(100,100), :compact => false)
```

```julia
large_df = DataFrame(rand(100,100))
WithIOContext(large_df, :displaysize => (9999,9999))
```
