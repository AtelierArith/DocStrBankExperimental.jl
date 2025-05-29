```
A = JopDwt(T, n...[, wt=wavelet(WT.haar, WT.Lifting)])
```

`A` is the N-D (N=1,2 or 3) wavelet transform operator, operating on the domain of type `T` and dimensions `n`.  The optional argument `wt` is the wavelet type. The supported wavelet types are `WT.haar` and `WT.db` (Daubechies).

# Notes

  * For 2 and 3 dimensional transforms the domain must be square.  In other-words, `size(dom,1)==size(dom,2)==size(dom,3)`.
  * If your domain is rectangular, please consider using 1D wavelet transforms in combination wih the kronecker product (`JopKron`).
  * The wavelet transform is provide by the Wavelets.jl package: `http://github.com/JuliaDSP/Wavelets.jl`
  * You may try other wavelet classes supported by `Wavelets.jl`; however, these have yet to be tested for correctness with respect to the

transpose.

# Example

```julia
A = JopDwt(Float64, 64, 64; wt=wavelet(WT.db5))
d = A*rand(domain(A))
```
