```
energy(f, x)
```

無条件サンプル $x \sim p_{\theta}(x)$ のエネルギーを計算します: $E(x)=-\text{LogSumExp}_y f_{\theta}(x)[y]$。
