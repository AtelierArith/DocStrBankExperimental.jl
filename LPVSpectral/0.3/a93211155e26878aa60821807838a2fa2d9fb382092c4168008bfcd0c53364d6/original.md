`S,f = ls_windowpsd(y,t,freqs; nw = 8, noverlap = -1, window_func=rect, estimator=ls_spectral, kwargs...)`

perform widowed spectral estimation using the least-squares method. `window_func` defaults to `Windows.rect`

`estimator` is the spectral estimatio function to use, default is `ls_spectral`. For sparse estimation, try `estimator = ls_sparse_spectral` See `ls_sparse_spectral` for more help. `kwargs` are passed to `estimator`.

See `ls_spectral` for additional help.
