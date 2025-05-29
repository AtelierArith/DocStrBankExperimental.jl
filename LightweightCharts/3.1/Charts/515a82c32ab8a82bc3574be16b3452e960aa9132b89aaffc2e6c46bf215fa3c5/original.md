```
lwc_bar(arg...; kw...) -> LWCChart
```

Creates a [`LWCChart`](@ref) from the passed `arg` that describes the corresponding candlestick values.

## Arguments

  * `timestamps::Vector{Union{Real,TimeType}}`
  * `open::Vector{Real}`
  * `high::Vector{Real}`
  * `low::Vector{Real}`
  * `close::Vector{Real}`
