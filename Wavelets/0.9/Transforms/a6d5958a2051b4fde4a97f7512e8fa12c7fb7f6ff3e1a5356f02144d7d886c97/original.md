Perform a maximal overlap discrete wavelet transform (MODWT) of the array `x`.  The wavelet type `wt` determines the transform type and the wavelet class, see `wavelet`. (Note that the wavelet filter coefficients are scaled by 1/√2 for the MODWT so that the transform maintains unit energy).

The number of transform levels `L` can be any number <= `maxmodwttransformlevels(x)` (the default value).

Returns an `n × L+1` matrix (where `n` is the length of `x`) with the wavelet coefficients for level j in column j.  The scaling coefficients are in the last (L+1th) column.
