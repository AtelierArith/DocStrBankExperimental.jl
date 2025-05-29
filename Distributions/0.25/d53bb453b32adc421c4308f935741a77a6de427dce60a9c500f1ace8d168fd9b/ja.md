```
pdfsquaredL2norm(d::Distribution)
```

分布 `d` の確率密度関数 $f(x)$ の L2 ノルムの二乗を返します：

$$
\int_{S} f(x)^{2} \mathrm{d} x
$$

ここで、$S$ は $f(x)$ のサポートです。
