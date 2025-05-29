```
mul!(f, p, fHat) -> f
```

Inplace transposed NFCT/NFST transforming the `R` dimensional array `fHat` to the `D` dimensional array `f`. The transformation is applied along `D-R+1` dimensions specified in the plan `p`.
