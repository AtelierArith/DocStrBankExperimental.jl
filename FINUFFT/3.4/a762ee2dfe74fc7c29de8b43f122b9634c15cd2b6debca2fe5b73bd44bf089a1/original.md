```
nufft3d1(xj      :: Array{Float64} or Array{Float32}, 
         yj      :: Array{Float64} or Array{Float32}, 
         zj      :: Array{Float64} or Array{Float32}, 
         cj      :: Array{ComplexF64} or Array{ComplexF32}, 
         iflag   :: Integer, 
         eps     :: Real,
         ms      :: Integer,
         mt      :: Integer,
         mu      :: Integer;
         kwargs...
        ) -> Array{ComplexF64}
```

Compute type-1 3D complex nonuniform FFT. This computes, to relative precision eps, via a fast algorithm:

```
                  nj
f[k1,k2,k3] =    SUM  c[j] exp(+-i (k1 x[j] + k2 y[j] + k3 z[j]))
                 j=1

for -ms/2 <= k1 <= (ms-1)/2,  -mt/2 <= k2 <= (mt-1)/2,
    -mu/2 <= k3 <= (mu-1)/2.
```

# Inputs

  * `xj`,`yj`,`zj` coordinates of nonuniform sources on the cube [-3pi,3pi)^3,           each a length-nj vector
  * `cj`       length-nj complex vector of source strengths. If length(cj)>nj,           expects a stack of vectors (eg, a nj*ntrans matrix) each of which is           transformed with the same source locations.
  * `iflag`    if >=0, uses + sign in exponential, otherwise - sign.
  * `eps`      relative precision requested (generally between 1e-15 and 1e-1)
  * `ms`,`mt`,`mu` number of Fourier modes requested in x,y and z; each may be           even or odd.           In either case the mode range is integers lying in [-m/2, (m-1)/2]
  * kwargs  (optional). See `nufft_opts` and https://finufft.readthedocs.io/en/latest/opts.html

# Output

  * size `(ms,mt,mu)` complex array of Fourier coefficients f         (ordering given by opts.modeord in each dimension; `ms` fastest, `mu`         slowest), or, if `ntrans>1`, a 4D array of size `(ms,mt,mu,ntrans)`.
