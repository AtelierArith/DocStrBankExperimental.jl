Generate alpha-sub-Gaussian (aSG) random numbers.

The implementation is based on https://github.com/ahmd-mahm/alpha-SGNm/blob/master/asgn.m

Reference: A. Mahmood and M. Chitre, "Generating random variates for stable sub-Gaussian processes with memory", Signal Processing, Volume 131, Pages 271-279, 2017. (https://doi.org/10.1016/j.sigpro.2016.08.016.)

# Arguments

  * `α`: characteristic exponent associated with the aSGN(m) process. This is

a scalar input and should lie within `collect(1.1:0.01:1.98)`.

  * `R`: covariance matrix of any adjacent `m+1` samples in an aSGN(m) process.

The dimension of `R` is equal to `m+1`. It should be a symmetric toeplitz matrix. The maximum acceptable size of `R` is `10x10`

  * `n`: number of samples required

# Examples

```jldoctest
julia> x = rand(AlphaSubGaussian(n=1000))
```
