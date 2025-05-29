```
PentaSphericalVariogram(; range, sill, nugget)
```

長さ単位の`range`、および`sill`と`nugget`の寄与を持つ五球面変動関数。

```
PentaSphericalVariogram(; ranges, rotation, sill, nugget)
```

代わりに、複数の`ranges`と`rotation`行列を使用して異方性モデルを構築します。

```
PentaSphericalVariogram(ball; sill, nugget)
```

代わりに、カスタムメトリック`ball`を使用します。

## 例

```julia
# 等方性モデル
PentaSphericalVariogram(range=2.0m)

# 異方性モデル
PentaSphericalVariogram(ranges=(1.0m, 2.0m))
```
