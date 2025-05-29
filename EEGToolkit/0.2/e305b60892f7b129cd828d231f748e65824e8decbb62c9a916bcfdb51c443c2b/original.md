Structure for amplitude spectrum estimations. Estimations are by default  one sided, with frequencies ranging from [0, fₛ/2]. The formula used is 

$$
\frac{2|H(f)|}{\sum_i w_i}
$$

with $w_i$ a Hanning window.

# Fields

  * `freq::Vector{<:AbstractFloat}`: Frequency range of the spectrum
  * `spectrum::Vector{<:AbstractFloat}`: Estimated spectral amplitude

# Constructors

`AmplitudeSpectrum(x::Vector{<:AbstractFloat}, sampling_rate::Integer, pad::Integer)` : Computes a direct PSD over a signal `x` with a given `sampling_rate`.
