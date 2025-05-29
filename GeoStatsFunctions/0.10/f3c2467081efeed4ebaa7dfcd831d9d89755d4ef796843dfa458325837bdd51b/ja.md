```
MaternVariogram(; range, sill, nugget, order)
```

`range`を長さ単位で、`sill`と`nugget`の寄与、およびベッセル関数の`order`を持つマテールン変動関数。

```
MaternVariogram(; ranges, rotation, sill, nugget, order)
```

または、複数の`ranges`と`rotation`行列を使用して異方性モデルを構築します。

```
MaternVariogram(ball; sill, nugget, order)
```

または、カスタムメトリック`ball`を使用します。

## 例

```julia
# 等方性モデル
MaternVariogram(range=2.0m)

# 異方性モデル
MaternVariogram(ranges=(1.0m, 2.0m))
```
