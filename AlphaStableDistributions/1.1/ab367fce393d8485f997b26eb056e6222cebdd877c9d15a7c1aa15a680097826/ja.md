```
fit(d::Type{<:AlphaSubGaussian}, x, m; p=1.0)
```

データに対して共分散法を用いてaSGN(m)モデルをフィットします。

共分散法は追加のパラメータ`p`を必要とします。理想的には、1 < p < αです。ほとんどの実用的なインパルスシナリオではp=1.0で十分です。`m`は共分散行列のラグの数です。

実装はhttps://github.com/ahmd-mahm/alpha-SGNm/blob/master/param_est/asgnfit.mに基づいています。

参考文献: A. Mahmood and M. Chitre, "Generating random variates for stable sub-Gaussian processes with memory", Signal Processing, Volume 131, Pages 271-279, 2017. (https://doi.org/10.1016/j.sigpro.2016.08.016.)
