```
GammaLikelihood(α::Real=1.0, l=exp)
```

固定形状 `α` のガンマ尤度。

$$
    p(y|f) = \operatorname{Gamma}(y | α, l(f))
$$

呼び出すと、形状 `α` とスケール `invlink(f)` のガンマ分布が返されます。
