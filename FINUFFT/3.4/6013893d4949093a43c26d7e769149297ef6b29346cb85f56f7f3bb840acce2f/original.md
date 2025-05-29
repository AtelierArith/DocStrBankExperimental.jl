```
nufft3d2(xj      :: Array{Float64} or Array{Float32}, 
         yj      :: Array{Float64} or Array{Float32}, 
         zj      :: Array{Float64} or Array{Float32}, 
         iflag   :: Integer, 
         eps     :: Real,
         fk      :: Array{ComplexF64} or Array{ComplexF32};
         kwargs...
        ) -> Array{ComplexF64}
```

Compute type-2 3D complex nonuniform FFT.  This computes, to relative precision eps, via a fast algorithm:

```
c[j] =   SUM   f[k1,k2,k3] exp(+/-i (k1 x[j] + k2 y[j] + k3 z[j]))
       k1,k2,k3
                       for j = 1,..,nj
 where sum is over -ms/2 <= k1 <= (ms-1)/2, -mt/2 <= k2 <= (mt-1)/2,
                  -mu/2 <= k3 <= (mu-1)/2.
```

# Inputs

  * `xj`,`yj`,`zj` coordinates of nonuniform targets on the cube [-3pi,3pi)^3,          each a vector of length nj
  * `fk`       complex Fourier coefficient array, whose size sets `(ms,mt,mu)`.          (Mode ordering given by opts.modeord, in each dimension.)          If a 4D array, 4th dimension sets `ntrans`, and each of `ntrans`          3D arrays is transformed with the same nonuniform targets.
  * `iflag`    if >=0, uses + sign in exponential, otherwise - sign.
  * `eps`      relative precision requested (generally between 1e-15 and 1e-1)
  * kwargs   (optional). See `nufft_opts` and https://finufft.readthedocs.io/en/latest/opts.html

# Output

  * complex vector c of size `(nj,)` giving answers at targets, or,         if `ntrans>1`, matrix of size `(nj,ntrans)`.
