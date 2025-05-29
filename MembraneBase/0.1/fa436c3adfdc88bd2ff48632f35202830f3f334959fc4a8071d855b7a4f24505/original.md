```
resample(transient::TransientStepData, num_datapoints, time_function)
```

Resample the data with some `time_function` spacing and linear interpolation between adjacent data points. Use this method when you have a ridiculous amount of data and need to slim it down while losing as little valuable information as possible.

# Arguments

  * `transient::TransientStepData`: TransientStepData used to resample
  * `num_datapoints::Integer`: number of resampled data points to be in the resulting TransientStepData (should always be less than what you currently have)
  * `time_function::Symbol`: how to weigh the time data...

      * `:Linear` will have even spacing from t=0 to t=num_datapoints
      * `:Root` will sample along the root of time (more information about the initial behavior will be kept)

          * It is usually best to use :Root for most scenarios and :Linear for quick scenarios
      * `:Log` will sample along the log_10 of time (much more info about initial behavior will be kept)

          * Reserve Log for extremely long timescales (think: on the order of *months* or *years*, not *days* or *weeks*)

This function assumes that time data is sorted in ascending order
