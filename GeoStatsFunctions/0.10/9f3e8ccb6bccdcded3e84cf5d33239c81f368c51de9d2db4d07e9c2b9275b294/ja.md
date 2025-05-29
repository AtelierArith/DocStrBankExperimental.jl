```
ExponentialVariogram(; range, sill, nugget)
```

長さ単位の`range`、および`sill`と`nugget`の寄与を持つ指数変動関数。

```
ExponentialVariogram(; ranges, rotation, sill, nugget)
```

または、複数の`ranges`と`rotation`行列を使用して異方性モデルを構築します。

```
ExponentialVariogram(ball; sill, nugget)
```

または、カスタムメトリック`ball`を使用します。

## 例

```julia
# 等方性モデル
ExponentialVariogram(range=2.0m)

# 異方性モデル
ExponentialVariogram(ranges=(1.0m, 2.0m))
```
