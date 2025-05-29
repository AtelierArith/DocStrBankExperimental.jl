```
AlignedSpan(sample_rate, span, mode::RoundingModeFullyContainedSampleSpans)
```

Constructs an `AlignedSpan` consisting of the full spans from each sample until the next sample occurs that are contained in the input span. 

For example:

```jldoctest
julia> using TimeSpans, AlignedSpans, Dates

julia> sample_rate = 1/30
0.03333333333333333

julia> input = TimeSpan(0, Second(30) + Nanosecond(1))
TimeSpan(00:00:00.000000000, 00:00:30.000000001)

julia> aligned = AlignedSpan(sample_rate, input, RoundFullyContainedSampleSpans)
AlignedSpan(0.03333333333333333, 1, 1)

julia> TimeSpan(aligned)
TimeSpan(00:00:00.000000000, 00:00:30.000000000)
```

Here, in contrast to the behavior for [`RoundInward`](@ref) or [`RoundSpanDown`](@ref), only one sample is included, since only one 30s-long "sample span" is fully included in the input span.
