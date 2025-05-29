A spectrogram is a matrix $S^{M \times F}$ where $M$ is the number of windows in  the windowing of a signal and $F$ is the length of the spectrum vector in any given window (i.e. the frequency resolution).  It is useful to observe spectral changes in time or to compute the  spectrum of time-regions of interest (e.g. only NREM periods in a sleep EEG).  The information available in direct PSD can be inferred from the spectrogram with ease.

For instance, let $f_1, f_2, \ldots, f_k$ be a strictly increasing sequence of frequencies. Assume these frequencies correspond to the column indexes $c_1, c_2, \ldots, c_k$ of $S$. Then the mean power in the frequency range  $[f_1, f_k]$ is

$$
\frac{1}{M} \sum_{i=1}^{M}\left[\frac{1}{c_k - c_1}\sum_{j=c_1}^{c_k} S_{ij}\right] = \frac{1}{M\big(c_k - c_1\big)}\sum_{i=1}^{M}\sum_{j=c_1}^{c_k} S_{ij}
$$

In this package, mean power in a frequency range is computed with the `mean_band_power` function.

# Fields

  * `time::Vector` : Time domain
  * `freq::Vector{<:AbstractFloat}`: Frequency domain
  * `spectrums::Matrix{<:AbstractFloat}`: Power spectrum. Rows are time and columns are frequency; the value in `spectrums[row, freq]` is the power at time window `row` for frequency `freq`.
  * `segment_length::Integer` : Length of each segment in time.
  * `aggregated_spectra::Vector{<:AbstractFloat}` : Spectral average (mean of rows)

# Constructors

  * `Spectrogram(segs::Vector{Vector{T}}, psd_function::Function; dB = false) where {T<:AbstractFloat}`: Given a sequence of windows $w_1, \ldots, w_k$ contained in the `segs` argument, computes the PSD within each window using a custom `psd_function`.
  * `Spectrogram(signal::Vector{<:AbstractFloat}, window_length::Integer, psd_function::Function; overlap::Union{AbstractFloat, Integer}=0, dB=false)`: Splits a signal into (potentially overlapping) segments of length `window_length` and computes the `Spectrogram` over this windowing using the first constructor. A custom `psd_function` is used within each window. Symmetry is enforced over the split signal, meaning that if the last segment is of length not equal to the rest, it is dropped. Thus, all windows are of equal length.
  * `function Spectrogram(ts::TimeSeries, window_length::Integer, psd_function::Function; kargs...)`: Wrapper constructor for a `TimeSeries` object.
