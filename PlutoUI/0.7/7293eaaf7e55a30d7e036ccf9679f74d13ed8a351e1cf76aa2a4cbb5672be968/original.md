```
WithIOContext(x, properties::Pair...)
```

A wrapper around `x` with extra IOContext properties set, just for the display of `x`.

!!! compat "PlutoUI 0.7.52"
    Before PlutoUI 0.7.52, `x` would be displayed using only the properties from `properties`, ignoring the properties from the IOContext used for the render. This has been fixed.


# Examples

```julia
WithIOContext(rand(100,100), :compact => false)
```

```julia
large_df = DataFrame(rand(100,100))
WithIOContext(large_df, :displaysize => (9999,9999))
```
