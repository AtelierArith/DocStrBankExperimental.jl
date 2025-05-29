```
Semicircle(r)
```

Wigner半円分布の半径パラメータ`r`を持つ確率密度関数は

$$
f(x; r) = \frac{2}{\pi r^2} \sqrt{r^2 - x^2}, \quad x \in [-r, r].
$$

```julia
Semicircle(r)   # 半径rのWigner半円分布

params(d)       # 半径パラメータを取得する、すなわち(r,)
```

外部リンク

  * [Wigner半円分布 - Wikipedia](https://en.wikipedia.org/wiki/Wigner_semicircle_distribution)
