```
jacobian!(r::JacobianDiffResult, F, x, cfg::JacobianConfig)
```

$$
F(x)
$$

と `F` の $x$ におけるヤコビアンを、`cfg` にある事前計算された値を使用して一度に計算し、結果を `r` に格納します。これは、両方の値を別々に計算するよりも速くなります。

### 例

```julia
cfg = GradientConfig(g)
r = GradientDiffResult(cfg)
gradient!(r, g, x, cfg)

value(r) == g(x)
gradient(r) == gradient(g, x, cfg)
```
