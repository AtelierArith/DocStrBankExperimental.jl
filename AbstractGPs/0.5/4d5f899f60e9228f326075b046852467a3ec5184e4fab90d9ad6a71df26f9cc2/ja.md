```
logpdf(lfgp::LatentFiniteGP, y::NamedTuple{(:f, :y)})
```

$$
    log p(y, f; x)
$$

ガウス過程の出力 `f` と観測 `y` の結合対数密度。
