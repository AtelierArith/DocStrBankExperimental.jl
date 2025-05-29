```
nufft3d3(xj      :: Array{Float64} or Array{Float32}, 
         yj      :: Array{Float64} or Array{Float32},
         zj      :: Array{Float64} or Array{Float32},
         cj      :: Array{ComplexF64} or Array{ComplexF32}, 
         iflag   :: Integer, 
         eps     :: Real,
         sk      :: Array{Float64} or Array{Float32},
         tk      :: Array{Float64} or Array{Float32},
         uk      :: Array{Float64} or Array{Float32};
         kwargs...
        ) -> Array{ComplexF64}
```

Compute type-3 3D complex nonuniform FFT. This computes, to relative precision eps, via a fast algorithm:

```
         nj
f[k]  =  SUM   c[j] exp(+-i (s[k] x[j] + t[k] y[j] + u[k] z[j])),
         j=1
                         for k = 1, ..., nk
```

# Inputs

  * `xj`,`yj`,`zj` coordinates of nonuniform sources in R^3, each a length-nj vector.
  * `cj`     complex `(nj,)` vector of source strengths. If length(cj)>nj,          expects a '(nj,ntrans)' matrix, each column of which is          transformed with the same source and target locations.
  * `iflag`    if >=0, uses + sign in exponential, otherwise - sign.
  * `eps`      relative precision requested (generally between 1e-15 and 1e-1)
  * `sk`,`tk,`uk` frequency coordinates of nonuniform targets in R^3,          each a length-nk vector.
  * kwargs   (optional). See `nufft_opts` and https://finufft.readthedocs.io/en/latest/opts.html

# Output

  * size `(nk,)` complex vector f values at targets, or, if `ntrans>1`,          a matrix of size `(nk,ntrans)`
