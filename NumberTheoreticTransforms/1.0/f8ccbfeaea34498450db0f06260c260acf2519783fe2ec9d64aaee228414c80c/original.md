```
fnt(x, g, q)
```

The Fermat Number Transform returns the same result as `ntt` function using more performant algorithm. When `q` has $ 2^{2^t}+1 $ form the calculation can be performed with O(N*log(N)) operation instead of O(N^2) for `ntt`.
