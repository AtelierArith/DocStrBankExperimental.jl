```
nufft1d2(xj      :: Array{Float64} or Array{Float32}, 
         iflag   :: Integer, 
         eps     :: Real,
         fk      :: Array{ComplexF64} or Array{ComplexF32};
         kwargs...
        ) -> Array{ComplexF64}
```

Compute type-2 1D complex nonuniform FFT.  This computes, to relative precision eps, via a fast algorithm:

```
c[j] = SUM   f[k1] exp(+/-i k1 x[j])      for j = 1,...,nj
        k1
 where sum is over -ms/2 <= k1 <= (ms-1)/2.
```

# Input

  * `xj`      location of nonuniform targets on interval [-3pi,3pi), length nj
  * `fk`      complex Fourier coefficients. If a vector, length sets `ms`         (with mode ordering given by opts.modeord). If a matrix, each         column is transformed with the same nonuniform targets.
  * `iflag`   if >=0, uses + sign in exponential, otherwise - sign.
  * `eps`     relative precision requested (generally between 1e-15 and 1e-1)
  * kwargs  (optional). See `nufft_opts` and https://finufft.readthedocs.io/en/latest/opts.html

# Output

  * complex `(nj,)` vector c of answers at targets, or,        if `ntrans>1`, matrix of size `(nj,ntrans)`.
