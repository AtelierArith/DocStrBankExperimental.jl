```
estimate_period(v::Vector, method, t=0:length(v)-1; kwargs...)
```

Estimate the period of the signal `v`, with accompanying time vector `t`, using the given `method`.

If `t` is an AbstractArray, then it is iterated through to ensure that it's evenly sampled (if necessary for the algorithm).  To avoid this, you can pass any `AbstractRange`, like a `UnitRange` or a `LinRange`, which are defined to be evenly sampled.

## Methods requiring evenly sampled data

These methods are faster, but some are error-prone.

  * `:periodogram` or `:pg`: Use the fast Fourier transform to compute a  periodogram (power-spectrum) of the given data.  Data must be evenly sampled.
  * `:multitaper` or `mt`: The multitaper method reduces estimation bias by using multiple independent estimates from the same sample. Data tapers are then windowed and the power spectra are obtained.  Available keywords follow: `nw` is the time-bandwidth product, and `ntapers` is the number of tapers. If `window` is not specified, the signal is tapered with `ntapers` discrete prolate spheroidal sequences with time-bandwidth product `nw`. Each sequence is equally weighted; adaptive multitaper is not (yet) supported. If `window` is specified, each column is applied as a taper. The sum of periodograms is normalized by the total sum of squares of `window`.
  * `:autocorrelation` or `:ac`: Use the autocorrelation function (AC). The value where the AC first comes back close to 1 is the period of the signal. The keyword `L = length(v)÷10` denotes the length of the AC (thus, given the default setting, this method will fail if there less than 10 periods in the signal). The keyword `ϵ = 0.2` (`\epsilon`) means that `1-ϵ` counts as "1" for the AC.
  * `:yin`: The YIN algorithm. An autocorrelation-based method to estimate the fundamental period of the signal. See the original paper [^CheveigneYIN2002] or the implementation [`yin`](@ref). Sampling rate is taken as `sr = 1/mean(diff(t))` if not given.

[^CheveigneYIN2002]: De Cheveigné, A., & Kawahara, H. (2002). YIN, a fundamental frequency estimator for

speech and music. The Journal of the Acoustical Society of America, 111(4), 1917-1930.

## Methods not requiring evenly sampled data

These methods tend to be slow, but versatile and low-error.

  * `:lombscargle` or `:ls`: Use the Lomb-Scargle algorithm to compute a periodogram.  The advantage of the Lomb-Scargle method is that it does not require an equally sampled dataset and performs well on undersampled datasets. Constraints have been set on the period, since Lomb-Scargle tends to have false peaks at very low frequencies.  That being said, it's a very flexible method.  It is extremely customizable, and the keyword arguments that can be passed to it are given [in the documentation](https://juliaastro.github.io/LombScargle.jl/stable/index.html#LombScargle.plan).
  * `:zerocrossing` or `:zc`: Find the zero crossings of the data, and use the average difference between zero crossings as the period.  This is a naïve implementation, with only linear interpolation; however, it's useful as a sanity check.  The keyword `line` controls where the "crossing point" is. It defaults to `mean(v)`.

For more information on the periodogram methods, see the documentation of DSP.jl and LombScargle.jl.
