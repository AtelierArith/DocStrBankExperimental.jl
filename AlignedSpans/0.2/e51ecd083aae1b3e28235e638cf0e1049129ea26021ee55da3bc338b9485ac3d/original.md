```
AlignedSpan(sample_rate, span, mode::ConstantSamplesRoundingMode)
```

Creates an `AlignedSpan` whose left endpoint is rounded according to `mode.start`, and whose right endpoint is determined so by the left endpoint and the number of samples, given by `AlignedSpans.n_samples(sample_rate, duration(span))`.

Interface: `span` may be of any type which which provides a method for [`AlignedSpans.start_index_from_time`](@ref) and `TimeSpans.duration`.

## More detailed information

This is designed so that if `AlignedSpan(sample_rate, span, mode::ConstantSamplesRoundingMode)` is applied to multiple `span`s, with the same `sample_rate`, and the same durations, then the resulting `AlignedSpan`'s will have the same number of samples.

For this reason, we ask for `TimeSpans.duration(span)` to be defined, rather than a `n_samples(span)` function: the idea is that we want to only using the duration and the starting time, rather than the *actual* number of samples in this particular `span`.

In contrast, [`RoundInward`](@ref) provides an `AlignedSpan` which includes only (and exactly) the samples which occur within `span` (as instants in time), while [`AlignedSpan(sample_rate, span, ::RoundingModeFullyContainedSampleSpans)`](@ref) provides an `AlignedSpan` consisting of the full spans from each sample until the next sample occurs that are contained in the input span.

If one wants to create a collection of consecutive, non-overlapping, `AlignedSpans` each with the same number of samples, then use [`consecutive_subspans`](@ref) instead.
