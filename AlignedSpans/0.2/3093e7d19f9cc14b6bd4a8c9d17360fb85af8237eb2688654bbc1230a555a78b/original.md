```
consecutive_overlapping_subspans(span::AlignedSpan, duration::Period,
                                 hop_duration::Period)
consecutive_overlapping_subspans(span::AlignedSpan, n_window_samples::Int, n_hop_samples::Int)
```

Create an iterator of `AlignedSpan` such that each `AlignedSpan` has `n_window_samples` (calculated as `n_samples(span.sample_rate, duration)` if `duration::Period` is supplied) samples, shifted by `n_hop_samples` (calculated as `n_samples(span.sample_rate, hop_duration)` if `hop_duration::Period` is supplied) samples between consecutive spans.

!!! warning
    When `n_samples(span)` is not an integer multiple of `n_window_samples`, only AlignedSpans with `n_window_samples` samples will be returned. This is analgous to `consecutive_subspans` with `keep_last=false`, which is not the default behavior for `consecutive_subspans`.


Note: If `hop_duration` cannot be represented as an integer number of samples, rounding will occur to ensure that all output AlignedSpans will have the same number of samples. When rounding occurs, the output `hop_duration` will be: `Nanosecond(n_samples(samp_rate, hop_duration) / samp_rate * 1e9)`
