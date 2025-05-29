```
 ts2hr(A::PeriodicTimeSeriesMatrix; atol = 0, rtol, n, squeeze = true) -> Ahr::HarmonicArray
```

Compute the harmonic (Fourier) approximation of a periodic matrix specified by a time series matrix.  The periodic matrix `A(t)` is specified as a continuous-time periodic time series matrix `A`,  with `m` matrices contained in the vector of matrices `A.values`, where `A.values[k]`  is the value of `A(t)` at time moment `(k-1)T/m`, with `T = A.period` being the period.  The resulting harmonic approximation `Ahr(t)` of `A(t)` has the form

```
                 p
 Ahr(t) = A_0 +  ∑ ( Ac_i*cos(i*t*2*π/T)+As_i*sin(i*2*π*t/T) ) 
                i=1
```

where `A_0` is the constant term (the mean value), `Ac_i` and `As_i` are the   coefficient matrices of the `i`-th cosinus and sinus terms, respectively.  The order of the approximation `p` is determined using the maximum order specified by `n`  (default: `n = (m-1)/2`) and the absolute and relative tolerances `atol` and `rtol`, as follows: `p` is the minimum between `n`, `(m-1)/2` and the maximum index `k`  such that `Ac_k` and/or `As_k` are nonzero. The tolerance used to assess nonzero elements is `tol = max(atol, rtol*maxnorm)`, where  `maxnorm` is the maximum norm of the matrices contained in `A.values`. The default values of tolerances are `atol = 0` and `rtol = 10*p*ϵ`, where `ϵ` is the working machine precision.

The resulting harmonic approximation `Ahr(t)` is returned in the harmonic array object `Ahr`  (see [`HarmonicArray`](@ref)). 
