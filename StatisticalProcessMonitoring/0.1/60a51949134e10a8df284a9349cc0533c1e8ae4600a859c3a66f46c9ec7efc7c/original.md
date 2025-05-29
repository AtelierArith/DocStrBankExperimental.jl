`Phase2` is a struct that holds the reference sample data and a sampling method, which is used to generate new observations from the reference data. 

### Arguments

  * `samp::AbstractSampling`: The sampling method to be used to generate new observations. Defaults to `Bootstrap()`.
  * `data`: The data from which observations need to be resampled.

### Examples

x = randn(500) PH2 = Phase2(data = x)
