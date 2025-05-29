`ls_cohere(y,u,t,freqs; nw = 10, noverlap = -1, estimator=ls_spectral, kwargs...)`

Perform spectral coherence estimation using the least-squares method.

`estimator` is the spectral estimatio function to use, default is `ls_spectral`. For sparse estimation, try `estimator = ls_sparse_spectral` See `ls_sparse_spectral` for more help. See also `ls_windowcsd` and `ls_spectral` for additional help.
