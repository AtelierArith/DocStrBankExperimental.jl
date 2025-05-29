```
apply_girf(g::GirfApplier, gradient_in, time_in, time_out, direction)

Function for predicting the gradient by applying the GIRF
This is done in one dimension only. Repeat this function for multiple dimensions
```

# Arguments

  * `g::GirfApplier` - GirfApplier containing GIRF data
  * `gradient_in` - input gradient waveform corresponding to time_in vector
  * `time_in` - time vector corresponding to input gradient waveform
  * `time_out` - output time vector desired (decimation)
  * `direction` - direction of the GIRF to use (x,y,z etc...)

# Outputs:

  * `grad_OUT_resampled` - Vector, gradient waveform with GIRF applied, in the time points of `time_out`.
