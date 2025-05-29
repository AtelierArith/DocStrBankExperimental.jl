```julia
firingPattern(
;
    start_time,
    n_pre,
    delay_pre,
    n_pos,
    delay_pos,
    delay,
    pulse,
    freq,
    causal,
    repeat_times,
    repeat_after
)

```

Generate external stimulation times and indices for pre/post stimulation. Usually used with `dataProtocol` (see folder examples in `examples/`).

# Output

  * `event_times` sorted list of external event times
  * `is_pre_or_post_index` whether the external events are pre (`true`) or post (`false`)
