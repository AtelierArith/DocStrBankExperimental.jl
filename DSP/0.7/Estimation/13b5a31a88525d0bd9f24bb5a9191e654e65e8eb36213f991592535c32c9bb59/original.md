```
esprit(x::AbstractArray, M::Integer, p::Integer, Fs::Real=1.0)
```

ESPRIT [^Roy1986] algorithm for frequency estimation. Estimation of Signal Parameters via Rotational Invariance Techniques

Given length N signal "x" that is the sum of p sinusoids of unknown frequencies, estimate and return an array of the p frequencies.

# Arguments

  * `x::AbstractArray`: complex length N signal array
  * `M::Integer`: size of correlation matrix, must be <= N.     The signal subspace is computed from the SVD of an M x (N-M+1) signal matrix     formed from N-M+1 length-M shifts of the signal x in its columns.     For best performance for 1 sinusoid, use M = (N+1)/3 (according to van der Veen and Leus).     For faster execution (due to smaller SVD), use small M or small N-M
  * `p::Integer`: number of sinusoids to estimate.
  * `Fs::Float64`: sampling frequency, in Hz.

# Returns

length p real array of frequencies in units of Hz.

[^Roy1986]: R Roy, A Paulraj and T Kailath, ESPRIT - A subspace approach to estimation of parameters of cisoids in noise, IEEE Trans. Acoustics, Speech, Signal Process., 34, 1340-1342 (1986). [url](http://ieeexplore.ieee.org/abstract/document/1164935/).
