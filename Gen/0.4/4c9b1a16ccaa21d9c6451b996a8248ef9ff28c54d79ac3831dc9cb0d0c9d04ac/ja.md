```
beta_uniform(theta::Real, alpha::Real, beta::Real)
```

`[0, 1]`の一様分布からのサンプルを確率`1-theta`で、パラメータ`alpha`と`beta`のベータ分布からのサンプルを確率`theta`で混合した`Float64`値をサンプリングします。
