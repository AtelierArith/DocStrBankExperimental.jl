`estimate_sdf(pts::Vector{Float64}, data, g; Ω=default_Ω(pts, g),              frequencies=default_frequencies(pts, g, Ω),              wts=nothing, kwargs...) -> (frequencies, estimates)`

Estimates the spectral density for the stationary process sampled at locations `pts` and with values given by `data` at frequencies `frequencies`. Each column in `data` is treated as an iid sample of the process and averaged in the final estimator. `Ω` is the resolution maximum for the window quadrature weights. 

Any provided keyword arguments are passed to `window_quadrature_weights` if `wts` is `nothing`, and ignored if `wts` is provided. See the docstrings for `window_quadrature_weights` for details on available kwargs. If `wts` is provided, the `Ω` arg also does nothing.
