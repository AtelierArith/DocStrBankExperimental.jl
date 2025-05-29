```
GradientDiffResult(cfg::GradientConfig)
```

$$
∇g(x)
$$

の計算中に、$g(x)$の評価に必要なほぼすべてを計算します。GradientDiffResultは、両方の値を保持するためのメモリを割り当てます。この構造体はまた、`gradient!`に$g(x)$と$∇g(x)$を保存するように指示します。

### 例

```julia
cfg = GradientConfig(g, x)
r = GradientDiffResult(cfg)
gradient!(r, g, x, cfg)

value(r) == g(x)
gradient(r) == gradient(g, x, cfg)
```

```
GradientDiffResult(grad::AbstractVector)
```

自分で勾配を保持するためのメモリを割り当てます。
