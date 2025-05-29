```
UnfoldSim.generate_events([rng::AbstractRNG, ]design::RepeatDesign{T})
```

For a `RepeatDesign`, iteratively call `generate_events` for the underlying {T} design and concatenate the results.

In case of `MultiSubjectDesign`, sort by subject. 
Please note that when using an `event_order_function`(e.g. `shuffle`) in a `RepeatDesign`, the corresponding RNG is shared across repetitions and not deep-copied for each repetition. As a result, the order of events will differ for each repetition.
