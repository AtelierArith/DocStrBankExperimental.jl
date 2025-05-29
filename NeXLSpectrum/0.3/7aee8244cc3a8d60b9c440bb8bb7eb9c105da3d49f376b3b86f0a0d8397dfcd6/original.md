```
fit_spectrum(spec::Spectrum, ffp::FilterFitPacket)::FilterFitResult
fit_spectrum(specs::AbstractVector{<:Spectrum}, ffp::FilterFitPacket)::Vector{FilterFitResult}
fit_spectra(specs::AbstractVector{<:Spectrum}, ffp::FilterFitPacket)::Vector{FilterFitResult}
```

Fit a `Spectrum` or a vector of `Spectrum` using the specified `FilterFitPacket`.  The result is a `FilterFitResult` structure which contains k-ratios, residuals, etc. 

```
fit_spectrum(hs::HyperSpectrum, ffp::FilterFitPacket; mode::Symbol=:Fast, zero = x -> max(0.0, x))::Array{KRatios}
```

  * `mode = :Fast` - Uses precomputed, filtered "vector" fit method.  No uncertainties are available.
  * `mode = :Intermediate` - Uses an optimized full fit without refits for negative k-ratios.
  * `mode = :Full` - Uses the full single spectrum fit algorithm including refitting when one or more k-ratio is less than zero.

Performs a filtered fit on a hyperspectrum returning an `Array{KRatios}`.

Selecting a mode:   :Fast is good for generating k-ratio maps or exploratory analysis of a k-ratio map. :Full is best when a   quantitative map of a high count hyperspectrum is desired.  Fit results for major elements are similar for   all three but differ for minor and trace elements.  Particularly when a k-ratio is slightly negative. This   negative k-ratio can effect the other k-ratios.  :Fast also works less well when many elements (>>10) (particularly   interfering elements) are included in the fit. Unfortunately, :Intermediate and :Full slow down when many elements   are fit - O(n(elements)²).

The following timing on a 512 x 512 x 2048 hyperspectrum fitting 21 elements with 33 distinct ROIs on a fast 6-core  laptop with 16 GiB memory give a relative feel for the speed of each algorithm.  Yes, :Fast is approximately 30 ×  faster than :Intermediate and used almost 80x less memory.  (64-bit references, 32-bit references use about 1/2  the memory and take about 4/5 the time.)

|         mode= | Threads | Run time (s) | Allocations | Allocated (GiB) | GC time |
| -------------:| -------:| ------------:| -----------:| ---------------:| -------:|
|         :Fast |       6 |         11.4 |      2.11 M |            4.72 |    3.0% |
| :Intermediate |       6 |        342.7 |     13.11 M |           364.4 |    4.2% |
|         :Full |       6 |        574.6 |       6.2 G |           862.9 |    5.5% |
|         :Fast |       1 |         25.5 |       2.1 M |            4.72 |    1.8% |
| :Intermediate |       1 |       1064.6 |      13.1 M |           364.4 |    0.9% |
|         :Full |       1 |       2186.2 |       6.2 G |           862.1 |    2.8% |
