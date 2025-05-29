```
mul!(fHat, p, f) -> fHat
```

`D` 次元配列 `f` を `R` 次元配列 `fHat` に変換するインプレース NFFT/NFCT/NFST/NNFFT。変換は、計画 `p` で指定された `D-R+1` 次元に沿って適用されます。
