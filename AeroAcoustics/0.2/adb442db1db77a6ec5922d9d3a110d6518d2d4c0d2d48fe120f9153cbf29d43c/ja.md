```
damas(env::Environment, b [,f<:AbstractArray, ω::Real]; maxiter=10)
```

`maxiter`回のDAMAS反復を`env.fn`のすべての周波数ビンまたは`f`の周波数に対して正確に実行します。`f`は`env.fn`の値の正確な（部分）集合と一致する値を含む必要があります。連続過剰緩和（SOR）は、緩和パラメータ`ω`で設定できます。デフォルトは`ω=1`で、これは緩和なしに対応します。

# 参考文献:

Brooks, T. F. et al. (2006). A deconvolution approach for the mapping of acoustic sources (DAMAS) determined from phased microphone arrays. J.Sound.Vib. 294(4), 856–879. https://doi.org/10.1016/j.jsv.2005.12.046
