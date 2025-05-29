```
energy(f, x, y::Int; agg=mean)
```

条件付きサンプル $x \sim p_{\theta}(x|y)$ のエネルギーを計算します: $E(x)=- f_{\theta}(x)[y]$。
