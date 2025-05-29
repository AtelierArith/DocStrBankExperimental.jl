```
 hr2bt(Ahr::HarmonicArray, N; P, nperiod]) -> Abt::Matrix
```

Build the block Toeplitz matrix of a harmonic (Fourier) array representation of a periodic matrix. 

The harmonic representation object `Ahr` of period `T` of a periodic matrix `Ahr(t)`  of subperiod `T′ = T/k` is in the form

```
                 p
 Ahr(t) = A_0 +  ∑ ( Ac_i*cos(i*t*2*π/T′)+As_i*sin(i*2*π*t/T′) ) ,
                i=1
```

where `k ≥ 1` is the number of subperiods. `Ahr(t)` can be equivalently expressed in the Fourier series representation form

```
            p
 Ahr(t) =   ∑ A_i*exp(im*i*ωh*t) ,
           i=-p
```

where `ωh = 2π/T′`, `A_i = (Ac_i-im*As_i)/2` and  `A_{-i} = (Ac_i+im*As_i)/2`.  `N` is the number of selected harmonic components (or Fourier modes) used for approximation.  The keyword parameter `P` is the number of full periods to be considered (default: `P = 1`) and `nperiod` is the number of subperiods to be considered, such that `1 ≤ nperiod ≤ k` (default: `nperiod = k`). 

For a given number `N ≥ p`, if the number of period is `P = 1` and the number of subperiods is `nperiod = 1`,  then the *banded* block Toeplitz matrix `Abt` with `(2N+1)×(2N+1)` blocks is constructed

```
       ( A_0  A_{-1} …  A_{-p}        0    )
       ( A_1   A_0             ⋱           )
       (  ⋮         ⋱            ⋱         )
 Abt = ( A_p             ⋱          A_{-p} )
       (        ⋱           ⋱         ⋮    )
       (  0        A_p      …         A_0  )
```

If `N < p`, then a truncated *full* block Toeplitz matrix is built using the first `N` harmonic components. 

Generally, for given `P ≥ 1` and  `nperiod ≥ 1`, the block Toeplitz matrix `Abt` is constructed with `(2N*np+1)×(2N*np+1)` blocks, with `np = P*nperiod`, such that each `A_i` is preceeded in its column by `np-1` zero blocks,  each `A_{-i}` is preceeded in its row by `np-1` zero blocks and all diagonal blocks are equal to`A_0`.   
