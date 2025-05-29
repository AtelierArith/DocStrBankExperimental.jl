```
SineHoleVariogram(; range, sill, nugget)
```

長さ単位の `range` と `sill` および `nugget` の寄与を持つサインホール変異関数。

```
SineHoleVariogram(; ranges, rotation, sill, nugget)
```

または、複数の `ranges` と `rotation` 行列を使用して異方性モデルを構築します。

```
SineHoleVariogram(ball; sill, nugget)
```

または、カスタムメトリック `ball` を使用します。

## 例

```julia
# 等方性モデル
SineHoleVariogram(range=2.0m)

# 異方性モデル
SineHoleVariogram(ranges=(1.0m, 2.0m))
```
