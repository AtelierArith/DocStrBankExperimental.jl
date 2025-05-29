```julia
track(
    signal,
    state,
    prn,
    sampling_frequency;
    post_corr_filter,
    intermediate_frequency,
    max_integration_time,
    min_integration_time,
    correlator_sample_shifts,
    early_late_index_shift,
    carrier_loop_filter_bandwidth,
    code_loop_filter_bandwidth,
    velocity_aiding
)

```

Track the signal `signal` based on the current tracking `state`, the sampling frequency `sampling_frequency` and PRN `prn`. Optional configurations are:

  * Post correlation filter `post_corr_filter` defaults to `get_default_post_corr_filter(...)`
  * Intermediate frequency `intermediate_frequency` defaults to 0Hz
  * Maximal integration time `max_integration_time` defaults to 1ms. The actual integration time can be less in order to find the secondary code or the bit shift. Once this is found the integration time is identical to the maximal integration time.
  * Minimal integration time `min_integration_time` defaults to 0.75ms. It's the minimal integration time, that leads to a valid correlation result. It is only used for the first integration period.
  * Sample shift of the correlator replica `correlator_sample_shifts` defaults to `get_correlator_sample_shifts(...)`
  * Bandwidth of the carrier loop `carrier_loop_filter_bandwidth` defaults to 18Hz
  * Bandwidth of the code loop `code_loop_filter_bandwidth` defaults to 1Hz
  * Velocity aiding `velocity_aiding` defaults to 0Hz
