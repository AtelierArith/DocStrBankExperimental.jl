```
RoundSpanDown = SpanRoundingMode(RoundDown, RoundDown)
```

This is a rounding mode where *both* ends of the continuous time interval are rounded downwards.

## Example

Consider a signal with sample rate 1 Hz.

```
Index       1   2   3   4   5
Time (s)    0   1   2   3   4
```

Now, consider the time span 1.5s (inclusive) to 2.5s (exclusive). Using brackets to highlight this span:

```
Index       1   2     3     4   5
Time (s)    0   1  [  2  )  3   4
```

In code, this span is described by

```jldoctest RoundSpanDown
julia> using AlignedSpans, Dates, TimeSpans

julia> ts = TimeSpan(Millisecond(1500), Millisecond(2500))
TimeSpan(00:00:01.500000000, 00:00:02.500000000)
```

If we round both ends of the interval down to the nearest sample, the start of the interval becomes 1s, and the stop of the interval becomes 2s. Thus, the associated samples are at indices `2:3`. And indeed,

```jldoctest RoundSpanDown
julia> aligned = AlignedSpan(1, ts, RoundSpanDown)
AlignedSpan(1.0, 2, 3)

julia> AlignedSpans.indices(aligned)
2:3
```

gives an `AlignedSpan` with indices `2:3`.
