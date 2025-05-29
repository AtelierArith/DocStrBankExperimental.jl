Compute periodogram from data `x`, using prewhitening, smoothing and recoloring. The data is fitted to an AR(1) model for prewhitening, and the residuals are used to compute a first-pass periodogram with smoothing.  The fitted coefficients are then used for recoloring.

##### Arguments

  * `x::Array`: An array containing the data to smooth
  * `window_len::Int(7)`: An odd integer giving the length of the window
  * `window::AbstractString("hanning")`: A string giving the window type. Possible values are `flat`, `hanning`, `hamming`, `bartlett`, or `blackman`

##### Returns

  * `w::Array{Float64}`: Fourier frequencies at which the periodogram is evaluated
  * `I_w::Array{Float64}`: The periodogram at frequences `w`
