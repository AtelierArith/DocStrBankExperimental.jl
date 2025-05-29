```
struct SegmentedTimeSpan
```

An immutable structure representing a long time span, split into units of equal length called *segments*. This structure is typically used to make consecutive calls to [`genpointings!`](@ref) and [`genpointings`](@ref).

The fields are the following:

  * `start_time` is the time of the first sample in the time span
  * `sampling_time` is the integration time for one sample
  * `segment_duration` is the duration of one segment
  * `num_of_segments` is the number of segments in the time span

The following example defines a time span of 1 year as the composition of multiple spans, each lasting one day:

```julia
sts = SegmentedTimeSpan(
    start_time = 0.0,
    sampling_time = 0.1,
    segment_duration = 24 * 3600,
    num_of_segments = 365,
)
```

Once a `SegmentedTimeSpan` has been constructed, it behaves like an array, whose elements are time ranges of type `StepRangeLen`. You can iterate over it, to run functions like [`genpointings`](@ref):

```julia
for cur_time_span in sts
    pointings = genpointings(PICO_SCANNING_STRATEGY, cur_time_span, ...)

    # "pointings" contain the pointings for the time span
end
```
