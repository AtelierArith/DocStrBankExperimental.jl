```
 FourierFunctionMatrix(Afun, T) -> A::FourierFunctionMatrix
```

Continuous-time Fourier function matrix representation.

The Fourier function matrix object `A` of period `T` is built using the Fourier series representation of a periodic matrix `Afun(t)` of subperiod `T′ = T/k`,  where each entry of `Afun(t)` has the form

```
         p
  a_0 +  ∑ ( ac_i*cos(i*t*2*π/T′)+as_i*sin(i*2*π*t/T′) ) ,
        i=1
```

where `k ≥ 1` is the number of subperiods (default: `k = 1`).    The matrix `Afun` containing the Fourier representation, the period `T` and the  number of subperiods `k` can be accessed via `A.M`, `A.period` and `A.nperiod`, respectively.
