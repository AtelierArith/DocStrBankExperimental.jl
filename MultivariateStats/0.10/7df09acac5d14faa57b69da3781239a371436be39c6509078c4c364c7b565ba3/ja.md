```
cov_whitening!(C, regcoef)
```

入力行列 `C` が計算中に上書きされる `cov_whitening(C, regcoef)` のインプレースバージョンです。`C` がもはや使用されない場合、これにより効率が向上する可能性があります。
