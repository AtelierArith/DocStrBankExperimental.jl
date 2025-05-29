```julia
regular_bearish_divergence(
    rf::ReversedSeries.ReversedFrame;
    indicator,
    high,
    upper,
    lower,
    age_threshold,
    gap_threshold,
    peak_threshold
) -> Any

```

Return true if regular bearish divergence on the given indicator was detected near index 1. Note that Bollinger Bands are used to help detect divergence, so their presence is required in the `rf` in addition to the indicator that's being tested for divergence.

# Keyword Arguments

|       argument |     default |                                 description |
| --------------:| -----------:| -------------------------------------------:|
|      indicator |    `:rsi14` | Name in `rf` for the indicator being tested |
|           high |        `:h` |        Name in `rf` for he OHLCV high value |
|          upper | `:bb_upper` |  Name in `rf` for the upper band of the BBs |
|          lower | `:bb_lower` |  Name in `rf` for the lower band of the BBs |
|  age_threshold |         `1` |                                           ? |
|  gap_threshold |    `(7,30)` |                                           ? |
| peak_threshold |       `9.0` |                                           ? |

# Example

```julia-repl
julia> regular_bearish_divergence(rf)
```
