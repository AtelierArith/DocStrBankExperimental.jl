```
modf!(iop, fop, op, rnd)
```

同時に `iop` を `op` の整数部分に、`fop` を `op` の小数部分に設定し、`iop` と `fop` の対応する精度で `rnd` の方向に丸めます（`trunc!(iop, op, rnd)` と `frac(fop, op, rnd)` に相当します）。変数 `iop` と `fop` は異なる必要があります。
