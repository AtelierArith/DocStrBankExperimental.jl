```
JohnsonSU(ξ, λ, γ, δ)
```

ジョンソンの $S_U$-分布は、パラメータ ξ, λ, γ および δ を持つ正規分布の変換です：

もし

$$
X = \lambda\sinh\Bigg( \frac{Z - \gamma}{\delta} \Bigg) + \xi
$$

ここで $Z \sim \mathcal{N}(0,1)$ の場合、$X \sim \operatorname{Johnson}(\xi, \lambda, \gamma, \delta)$ となります。

```julia
JohnsonSU()           # JohnsonSU(0, 1, 0, 1) と同等
JohnsonSU(ξ, λ, γ, δ) # パラメータ ξ, λ, γ および δ を持つジョンソンの S_U-分布

params(d)           # パラメータを取得します。すなわち (ξ, λ, γ, δ)
shape(d)            # 形状パラメータを取得します。すなわち ξ
scale(d)            # スケールパラメータを取得します。すなわち λ
```

外部リンク

  * [ジョンソンの $S_U$-分布 - Wikipedia](http://en.wikipedia.org/wiki/Johnson%27s_SU-distribution)
