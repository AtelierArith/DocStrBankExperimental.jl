```
RoundInward = SpanRoundingMode(RoundUp, RoundDown)
```

This is a rounding mode where both ends of the continuous time interval are rounded "inwards" to construct the largest span of indices such that all samples, as instants of time, occur within the span.

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

```jldoctest RoundInward
julia> using AlignedSpans, Dates, TimeSpans

julia> ts = TimeSpan(Millisecond(1500), Millisecond(2500))
TimeSpan(00:00:01.500000000, 00:00:02.500000000)
```

The only sample within the span is at index 3. And indeed,

```jldoctest RoundInward
julia> aligned = AlignedSpan(1, ts, RoundInward)
AlignedSpan(1.0, 3, 3)

julia> AlignedSpans.indices(aligned)
3:3
```

gives an `AlignedSpan` with indices `3:3`.
