```
 ffm2hr(Afun::FourierFunctionMatrix; atol = 0, rtol = √ϵ, squeeze = true) -> Ahr::HarmonicArray
```

Compute the harmonic (Fourier) representation of a Fourier periodic matrix object. 

The Fourier function matrix object `Afun` of period `T` is built using the Fourier series representation of a periodic matrix `Afun(t)` of subperiod `T′ = T/k`,  where each entry of `Afun(t)` has the form

```
         p
  a_0 +  ∑ ( ac_i*cos(i*t*2*π/T′)+as_i*sin(i*2*π*t/T′) ) ,
        i=1
```

where `k ≥ 1` is the number of subperiods (default: `k = 1`).   

The harmonic array object `Ahr` of period `T` is built using the harmonic representation of a periodic matrix `Ahr(t)` of subperiod `T′′ = T/k′` in the form

```
                 p′
 Ahr(t) = A_0 +  ∑ ( Ac_i*cos(i*t*2*π/T′′)+As_i*sin(i*2*π*t/T′′) ) ,
                i=1
```

where `p′` is the maximum index `j`, such that `Ac_j` and/or `As_j` are nonzero. The tolerance used to assess nonzero elements is `tol = max(atol, rtol*maxnorm)`, where  `maxnorm` is the maximum absolute value of the coefficients `ac_i` and `as_i` in `Afun(t)`. The default values of tolerances are `atol = 0` and `rtol = √ϵ`, where `ϵ` is the working machine precision. The resulting harmonic approximation `Ahr(t)` is returned in the harmonic array object `Ahr`  (see [`HarmonicArray`](@ref)). 
