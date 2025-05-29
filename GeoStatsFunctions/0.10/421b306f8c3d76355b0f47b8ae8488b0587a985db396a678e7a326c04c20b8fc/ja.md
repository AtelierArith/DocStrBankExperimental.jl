```
GaussianVariogram(; range, sill, nugget)
```

長さ単位の`range`を持つガウス変動関数で、`sill`と`nugget`の寄与があります。

```
GaussianVariogram(; ranges, rotation, sill, nugget)
```

また、複数の`ranges`と`rotation`行列を使用して異方性モデルを構築します。

```
GaussianVariogram(ball; sill, nugget)
```

また、カスタムメトリック`ball`を使用します。

## 例

```julia
# 等方性モデル
GaussianVariogram(range=2.0m)

# 異方性モデル
GaussianVariogram(ranges=(1.0m, 2.0m))
```
