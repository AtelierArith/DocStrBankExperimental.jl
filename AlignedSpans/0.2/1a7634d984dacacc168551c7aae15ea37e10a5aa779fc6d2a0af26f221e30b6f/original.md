```
RoundFullyContainedSampleSpans
```

This is a special rounding mode which differs from the other rounding modes by associating each sample with a *span* (from the instant the sample occurs until just before the next sample occurs), and rounding inwards to the "sample spans" that are fully contained in the input span.

This is in some sense a stricter form of inward rounding than provided by [`RoundInward`](@ref).

## Example

Consider a signal with sample rate 1 Hz.

```
Index       1   2   3   4   5
Time (s)    0   1   2   3   4
```

Normally, we consider each sample to occur at an instant of time. For `RoundFullyContainedSampleSpans`, we consider the span between a sample occurring and the next sample. (This usually does not make sense for digital sensors, but can make sense for things like hypnograms in which a sample summarizes some region of time).

Thus, to each index (each sample), we associate a 1s closed-open span of time:

```
Index        1     2     3     4     5
Span (s)    [0   )[1   )[2   )[3   )[4    )
```

The span durations are `1/sample_rate`, which is 1s in this example.

Now, consider the input time span 1.5s (inclusive) to 3.5s (exclusive). Using brackets to highlight this span:

```
Index        1     2     3     4     5
Span (s)    [0   )[1   )[2   )[3   )[4    )
Time (s)     0     1  [  2     3  )  4
```

This input span contains only one sample-span, namely `[2s, 3s)`. The span from `[1s, 2)` is not fully contained, nor is the span from `[3s, 4s)`.

Thus, in this scenario, `RoundFullyContainedSampleSpans` would give a single sample, that at index 3, associated to `[2s, 3s)`.

In code, this span is described by

```jldoctest RoundFullyContainedSampleSpans
julia> using AlignedSpans, Dates, TimeSpans

julia> ts = TimeSpan(Millisecond(1500), Millisecond(3500))
TimeSpan(00:00:01.500000000, 00:00:03.500000000)

julia> aligned = AlignedSpan(1, ts, RoundFullyContainedSampleSpans)
AlignedSpan(1.0, 3, 3)

julia> AlignedSpans.indices(aligned)
3:3
```
