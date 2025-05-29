```
gradient!(r::GradientDiffResult, g, x, cfg::GradientConfig)
```

$$
g(x)
$$

と `g` の勾配を `cfg` にある事前計算された値を使用して同時に計算し、その結果を `r` に格納します。これは、両方の値を別々に呼び出すよりも速くなります。

### 例

```julia
cfg = GradientConfig(g)
r = GradientDiffResult(r)
gradient!(r, g, x, cfg)

value(r) == g(x)
gradient(r) == gradient(g, x, cfg)
```
