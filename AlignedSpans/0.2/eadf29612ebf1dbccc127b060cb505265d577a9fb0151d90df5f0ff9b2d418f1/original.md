```
consecutive_subspans(span::AlignedSpan, duration::Period; keep_last=true)
consecutive_subspans(span::AlignedSpan, n_window_samples::Int; keep_last=true)
```

Creates an iterator of `AlignedSpan` such that each `AlignedSpan` has consecutive indices which cover the original `span`'s indices (when `keep_last=true`).

If `keep_last=true` (the default behavior), then the last span may have fewer samples than the others, and

  * Each span has `n_window_samples` samples (which is calculated as `n_samples(span.sample_rate, duration)` if `duration::Period` is supplied), except possibly

the last one, which may have fewer.

  * The number of subspans is given by `cld(n_samples(span), n_window_samples)`,
  * The number of samples in the last subspan is `r = rem(n_samples(span), n_window_samples)` unless `r=0`, in which

case the the last subspan has the same number of samples as the rest, namely `n_window_samples`.

  * All of the indices of `span` are guaranteed to be covered by exactly one subspan

If `keep_last=false`, then all spans will have the same number of samples:

  * Each span has `n_window_samples` samples (which is calculated as `n_samples(span.sample_rate, duration)` if `duration::Period` is supplied)
  * The number of subspans is given by `fld(n_samples(span), n_window_samples)`
  * The last part of the `span`'s indices may not be covered (when we can't fit in another subspan of length `n_window_samples`)
