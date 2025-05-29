```
squeeze([T=ComplexF64,] b::SpinBasis, z)
```

Squeezing operator $S(z)=\exp{\left(\frac{z^*\hat{J_-}^2 - z\hat{J}_+}{2 N}\right)}$ for the  specified Spin-$N/2$ basis with optional data type `T`, computed as the matrix exponential. Too large squeezing ($|z| > \sqrt{N}$) will create an oversqueezed state.
