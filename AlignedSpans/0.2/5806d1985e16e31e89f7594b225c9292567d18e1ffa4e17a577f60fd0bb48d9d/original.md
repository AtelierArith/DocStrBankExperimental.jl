```
AlignedSpan(sample_rate, span, mode::SpanRoundingMode)
```

Creates an `AlignedSpan` by rounding the left endpoint according to `mode.start`, and the right endpoint by `mode.stop`.

If `mode.start==RoundUp`, then the left index of the resulting span is guaranteed to be inside `span`. This is accomplished by checking if the left endpoint of the span is exclusive, and if so, incrementing the index after rounding when necessary.

Likewise, if `mode.stop==RoundDown`, then the right index of the resulting span is guaranteed to be inside `span`. This is accomplished by checking if the right endpoint of the span is exclusive, and if so, decrementing the index after rounding when necessary.

Note: `span` may be of any type which which provides methods for `AlignedSpans.start_index_from_time` and `AlignedSpans.stop_index_from_time`.

!!! warning
    If the input `span` is not sample-aligned, meaning the `start` and `stop` of the input span are not exact multiples of the sample rate, the results can be non-intuitive at first. Each underlying sample is considered to occur at some instant in time (not, e.g. over a span of duration of `1/sample_rate`), and the rounding is relative to the samples themselves.

    So for example:

    ```jldoctest
    julia> using TimeSpans, AlignedSpans, Dates

    julia> sample_rate = 1/30
    0.03333333333333333

    julia> input = TimeSpan(0, Second(30) + Nanosecond(1))
    TimeSpan(00:00:00.000000000, 00:00:30.000000001)

    julia> aligned = AlignedSpan(sample_rate, input, RoundInward) # or RoundSpanDown
    AlignedSpan(0.03333333333333333, 1, 2)

    julia> TimeSpan(aligned)
    TimeSpan(00:00:00.000000000, 00:01:00.000000000)

    ```

    Even though we have specified `RoundInward` or `RoundSpanDown`, both of which round the right-endpoint down, the resulting sample-aligned `TimeSpan(aligned)` is `TimeSpan(0, Second(60))`.

    How can this be? Clearly `Second(60) > Second(30) + Nanosecond(1)`, so what is going on?

    To understand this, note that at 1/30Hz, the samples occur at 00:00, 00:30, 00:60, and so forth. The original input span includes *two* samples, the one at 00:00 and the one at 00:30. Rounding inward to include only samples that occur within the span means including both samples (see [`RoundFullyContainedSampleSpans`](@ref) for alternate behavior).

    When converting back to TimeSpans, AlignedSpans canonicalizes `AlignedSpan(1/30, 1, 2)` as `TimeSpan(0, Second(60))`, representing these two samples as the time from the first sample until just before the not-included sample-3 (which occurs at `Second(60)`), using that `TimeSpan`'s exclude their right endpoint.

    AlignedSpans could make a different choice to e.g. canonicalize samples to only add an additional nanosecond, but that has its own issue (e.g. `TimeSpan(AlignedSpan(sample_rate, 1, 2))` and `TimeSpan(AlignedSpan(sample_rate, 3, 4))` would not be consecutive).


See also [`AlignedSpan(sample_rate, span, mode::RoundingModeFullyContainedSampleSpans)`](@ref).
