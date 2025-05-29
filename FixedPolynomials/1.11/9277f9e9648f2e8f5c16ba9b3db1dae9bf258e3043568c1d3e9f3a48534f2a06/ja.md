```
JacobianDiffResult(cfg::GradientConfig)
```

ヤコビアン $J_F(x)$ の計算中に、$F(x)$ の評価に必要なほぼすべてを計算します。`JacobianDiffResult` は、両方の値を保持するためのメモリを割り当てます。この構造体はまた、`jacobian!` に $F(x)$ と $J_F(x)$ を保存するように指示します。

### 例

```julia
cfg = JacobianConfig(F, x)
r = JacobianDiffResult(cfg)
jacobian!(r, F, x, cfg)

value(r) == map(f -> f(x), F)
jacobian(r) == jacobian(F, x, cfg)
```

```
JacobianDiffResult(value::AbstractVector, jacobian::AbstractMatrix)
```

値とヤコビアンを保持するためのメモリを自分で割り当てます。
