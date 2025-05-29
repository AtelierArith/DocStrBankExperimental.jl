```
 HarmonicArray(A0, Ac, As, T) -> A::HarmonicArray
```

Construct a harmonic array representation from the harmonic components.

The harmonic array object `A` is built for  the harmonic representation `Ahr(t)` of a periodic matrix of period `T` in the form

```
                 p
 Ahr(t) = A_0 +  ∑ ( Ac_i*cos(i*t*2*π/T)+As_i*sin(i*2*π*t/T) ) ,
                i=1
```

where the constant term `A_0` is contained in the real matrix `A0`, and `Ac` and `As` are vectors of real matrices such that the `i`-th (cosinus) coefficient matrix  `Ac_i` is contained in `Ac[i]` and the `i`-th (sinus) coefficient matrix  `As_i` is contained in `As[i]`. `p` is the maximum of length of the vectors of matrices `Ac` and `As`.  If the length of `Ac` or `As` is less than `p`, then zero trailing matrices are assumed in the respective matrix.  All component matrices must have the same dimensions. The complex matrix containing the harmonic components and the period `T`  can be accessed via `A.values` and `A.period`, respectively.
