Smooth the data in x using convolution with a window of requested size and type.

##### Arguments

  * `x::Array`: An array containing the data to smooth
  * `window_len::Int(7)`: An odd integer giving the length of the window
  * `window::AbstractString("hanning")`: A string giving the window type. Possible values are `flat`, `hanning`, `hamming`, `bartlett`, or `blackman`

##### Returns

  * `out::Array`: The array of smoothed data
