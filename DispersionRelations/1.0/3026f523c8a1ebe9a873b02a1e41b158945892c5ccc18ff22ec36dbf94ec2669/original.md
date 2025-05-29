fit*complex*frequency(t, E, use_peaks=nothing)

Find the best fit to an exponential model for the given energy trace. That is, this function finds a fit of the form E ≈ E₀ * exp(iωt).

If `use_peaks` is provided, it serves as a range or vector of which peaks to use during the fitting process. If it is omitted, the function uses a heuristic to find the range of consecutive peaks which provides the most stable fit.

Return a pair `(line, ω)` where     - `line` is a flat line that passes through the peaks used for the fit     - `ω` is the complex frequency of the estimated exponential
