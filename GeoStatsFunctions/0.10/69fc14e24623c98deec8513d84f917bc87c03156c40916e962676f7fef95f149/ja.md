```
CubicVariogram(; range, sill, nugget)
```

長さ単位の`range`と`sill`および`nugget`の寄与を持つ立方体変動関数。

```
CubicVariogram(; ranges, rotation, sill, nugget)
```

代わりに、複数の`ranges`と`rotation`行列を使用して異方性モデルを構築します。

```
CubicVariogram(ball; sill, nugget)
```

代わりに、カスタムメトリック`ball`を使用します。

## 例

```julia
# 等方性モデル
CubicVariogram(range=2.0m)

# 異方性モデル
CubicVariogram(ranges=(1.0m, 2.0m))
```
