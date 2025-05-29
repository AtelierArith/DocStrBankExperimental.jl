```
 HarmonicArray(Ahr, T; nperiod = k) -> A::HarmonicArray
```

Continuous-time harmonic array representation.

The harmonic array object `A` of period `T` is built using the harmonic representation of a periodic matrix `Ahr(t)` of subperiod `T′ = T/k` in the form

```
                 p
 Ahr(t) = A_0 +  ∑ ( Ac_i*cos(i*t*2*π/T′)+As_i*sin(i*2*π*t/T′) ) ,
                i=1
```

where `k ≥ 1` is the number of subperiods (default: `k = 1`).                    The `m×n×(p+1)` complex array `Ahr` contains the harmonic components as follows: `Ahr[:,:,1]` contains the constant term `A_0` (the mean value) and the real and imaginary parts of `Ahr[:,:,i+1]`   for `i = 1, ..., p` contain the coefficient matrices `Ac_i` and `As_i`, respectively.  The complex matrix `Ahr` containing the harmonic components, the period `T` and the  number of subperiods `k` can be accessed via `A.values`, `A.period` and `A.nperiod`, respectively.
