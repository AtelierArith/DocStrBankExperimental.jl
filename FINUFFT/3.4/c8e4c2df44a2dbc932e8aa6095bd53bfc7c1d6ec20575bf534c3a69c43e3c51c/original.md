```
nufft1d3(xj      :: Array{Float64} or Array{Float32}, 
         cj      :: Array{ComplexF64} or Array{ComplexF32}, 
         iflag   :: Integer, 
         eps     :: Real,
         sk      :: Array{Float64} or Array{Float32};
         kwargs...
        ) -> Array{ComplexF64}
```

Compute type-3 1D complex nonuniform FFT. This computes, to relative precision eps, via a fast algorithm:

```
         nj
f[k]  =  SUM   c[j] exp(+-i s[k] x[j]),      for k = 1, ..., nk
         j=1
```

# Inputs

  * `xj`       locations of nonuniform sources on R (real line), length-nj vector.
  * `cj`       length-nj complex vector of source strengths. If length(cj)>nj,           expects a size `(nj,ntrans)` matrix each column of which is           transformed with the same source and target locations.
  * `iflag`    if >=0, uses + sign in exponential, otherwise - sign.
  * `eps`      relative precision requested (generally between 1e-15 and 1e-1)
  * `sk`       frequency locations of nonuniform targets on R, length-nk vector.
  * kwargs   (optional). See `nufft_opts` and https://finufft.readthedocs.io/en/latest/opts.html

# Output

  * complex vector f size '(nk,)`of values at targets, or, if`ntrans>1`,          a matrix of size`(nk,ntrans)`
