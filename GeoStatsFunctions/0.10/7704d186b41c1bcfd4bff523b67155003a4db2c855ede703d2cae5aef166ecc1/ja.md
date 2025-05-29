```
SphericalVariogram(; range, sill, nugget)
```

長さ単位の`range`と`sill`および`nugget`の寄与を持つ球状変動関数。

```
SphericalVariogram(; ranges, rotation, sill, nugget)
```

または、複数の`ranges`と`rotation`行列を使用して異方性モデルを構築します。

```
SphericalVariogram(ball; sill, nugget)
```

または、カスタムメトリック`ball`を使用します。

## 例

```julia
# 等方性モデル
SphericalVariogram(range=2.0m)

# 異方性モデル
SphericalVariogram(ranges=(1.0m, 2.0m))
```
