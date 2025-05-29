Structure for PSD estimations. Estimations are by default  one sided, with frequencies ranging from [0, fₛ/2].

The default formula is 

$$
\frac{2|H(f)|^2}{\zeta \sum_i w_i^2}
$$

with $w_1, \ldots, w_n$ a Hanning window and $\zeta$ a normalization factor which defaults  to $1$.  

Barlett or Welch's mehtod can be used, where the formula  becomes 

$$
\frac{1}{M K \varphi} \sum_i^M \left[ \frac{2|H_i(f)|^2}{ \sum_i w_i^2} \right]
$$

where $w_1, \ldots, w_n$ a Hanning window, $M$ the number of segments, $K$ the number of samples per segment, $H_i(f)$ the FFT of the $i$th segment of the signal, and $\varphi$ a normalization factor defaulting to `1`.

# Fields

  * `freq::Vector{<:AbstractFloat}`: Frequency range of the spectrum
  * `spectrum::Vector{<:AbstractFloat}` : Estimated spectral density in dB.

# Constructors

  * `PSD(x::Vector{<:AbstractFloat}, fs::Integer; window_function::Function = hanning, pad::Integer=0, normalization::Real=1)`: Computes PSD estimation of a signal `x` with sampling rate `fs`. A `window_function` is applied to the signal, defaulting to a Hanning window. The signal may be padded to an optional length `pad` (defaults to zero, i.e. no padding). A `Real` `normalization` is added to the denominator, which defaults to `1`.
  * `PSD(segs::Vector{Vector{T}}, fs::Integer; window_function=hanning, normalization::Real=1) where {T<:AbstractFloat}`: Computes the average spectrum of the segment vectors `segs`. The estimation is normalized with a `normalization` that defaults to $1$. The `window_function` is applied to all segments prior to their PSD estimation.

`PSD(x::Vector{<:AbstractFloat}, fs::Integer, seg_length::Integer; overlap::Union{<:AbstractFloat,Integer} = 0.5, window_function::Function=hanning, normalization::Real=1)`: Segments the signal `x` into segments of length `seg_length`, with an overlap of `overlap` which defaults to 0.5 (half the segment length). After signal segmentation, the average spectrum of the resulting segments is returned. A `window_function` is applied to all segments prior to their PSD estimation, defaulting to a Hanning window. The final estimation is normalized with a `normalization` factor that defaults to `1`.

  * `PSD(ts::TimeSeries; kargs...)` : Wrapper to apply the first or second constructor to a TimeSeries signal.
  * `PSD(ts::TimeSeries, seg_length::Integer; kargs...)`: Wrapper to apply the third constructor to a TimeSeries signal.
  * `PSD(freq::Vector{<:AbstractFloat},  spectrum::Vector{<:AbstractFloat})`: Direct constructor.
