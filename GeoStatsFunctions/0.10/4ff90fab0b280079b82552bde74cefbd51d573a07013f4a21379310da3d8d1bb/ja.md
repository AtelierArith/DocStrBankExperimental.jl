```
CircularVariogram(; range, sill, nugget)
```

長さ単位の`range`、および`sill`と`nugget`の寄与を持つ円形変動関数。

```
CircularVariogram(; ranges, rotation, sill, nugget)
```

または、複数の`ranges`と`rotation`行列を使用して異方性モデルを構築します。

```
CircularVariogram(ball; sill, nugget)
```

または、カスタムメトリック`ball`を使用します。

## 例

```julia
# 等方性モデル
CircularVariogram(range=2.0m)

# 異方性モデル
CircularVariogram(ranges=(1.0m, 2.0m))
```
