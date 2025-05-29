```
is_recording([current_span()])
```

Returns `true` if this span `s` is recording information like [`Event`](@ref) operations, attribute modification using [`setindex!`](@ref), etc.
