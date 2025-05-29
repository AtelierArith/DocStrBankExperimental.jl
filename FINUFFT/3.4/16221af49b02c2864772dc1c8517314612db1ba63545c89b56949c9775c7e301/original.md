```
nufft1d1(xj      :: Array{Float64} or Array{Float32}, 
         cj      :: Array{ComplexF64} or Array{ComplexF32}, 
         iflag   :: Integer, 
         eps     :: Real,
         ms      :: Integer;
         kwargs...
        ) -> Array{ComplexF64} or Array{ComplexF32}
```

Compute type-1 1D complex nonuniform FFT.  This computes, to relative precision eps, via a fast algorithm:

```
          nj
f(k1) =  SUM c[j] exp(+/-i k1 x(j))  for -ms/2 <= k1 <= (ms-1)/2
         j=1
```

# Inputs

  * `xj`      locations of nonuniform sources on interval [-3pi,3pi), length nj
  * `cj`      length-nj complex vector of source strengths. If length(cj)>nj,         expects a stack of vectors (eg, a nj*ntrans matrix) each of which is         transformed with the same source locations.
  * `iflag`   if >=0, uses + sign in exponential, otherwise - sign.
  * `eps`     relative precision requested (generally between 1e-15 and 1e-1)
  * `ms`      number of Fourier modes computed, may be even or odd;         in either case, mode range is integers lying in [-ms/2, (ms-1)/2]
  * kwargs  (optional). See `nufft_opts` and https://finufft.readthedocs.io/en/latest/opts.html

# Output

  * size `(ms,)` complex vector of Fourier coefficients f, or, if         `ntrans>1`, matrix of size `(ms,ntrans)`.
