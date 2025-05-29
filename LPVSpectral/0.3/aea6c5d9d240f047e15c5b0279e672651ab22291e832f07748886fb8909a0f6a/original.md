`ls_windowcsd(y,u,t,freqs; nw = 10, noverlap = -1, window_func=rect, estimator=ls_spectral, kwargs...)`

Perform windowed cross spectral density estimation using the least-squares method.

`y` and `u` are the two signals to be analyzed and `t::AbstractVector` are their sampling points `window_func` defaults to `Windows.rect`

`estimator` is the spectral estimatio function to use, default is `ls_spectral`. For sparse estimation, try `estimator = ls_sparse_spectral` See `ls_sparse_spectral` for more help.

See `ls_spectral` for additional help.
