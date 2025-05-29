```
mul!(fHat, p, f) -> fHat
```

Inplace NFFT/NFCT/NFST/NNFFT transforming the `D` dimensional array `f` to the `R` dimensional array `fHat`. The transformation is applied along `D-R+1` dimensions specified in the plan `p`.
