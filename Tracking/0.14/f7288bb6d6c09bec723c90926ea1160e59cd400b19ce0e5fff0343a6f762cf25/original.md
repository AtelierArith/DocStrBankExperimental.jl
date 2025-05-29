```julia
TrackingState(
    system,
    carrier_doppler,
    code_phase;
    code_doppler,
    carrier_phase,
    carrier_loop_filter,
    code_loop_filter,
    sc_bit_detector,
    num_ants,
    correlator,
    integrated_samples,
    prompt_accumulator,
    cn0_estimator
)

```

Convenient TrackingState constructor. Mandatory parameters are the GNSS system, the carrier doppler `carrier_doppler` and the code phase `code_phase`. Optional parameters are

  * Code doppler `code_doppler`, that defaults to carrier doppler multiplied with the code / center frequency ratio
  * Carrier phase `carrier_phase`, that defaults to 0
  * Carrier loop filter `carrier_loop_filter`, that defaults to the `ThirdOrderBilinarLF()`
  * Code loop filter `code_loop_filter`, that defaults to the `SecondOrderBilinearLF()`
  * Number of antenna elemants `num_ants`, that defaults to `NumAnts(1)`
  * Correlator `correlator`, that defaults to `get_default_correlator(...)`
  * Integrated samples `integrated_samples`, that defaults to 0
  * Prompt accumulator for bit detection `prompt_accumulator`, that defaults to 0
  * CN0 estimator `cn0_estimator`, that defaults to `MomentsCN0Estimator(20)`
