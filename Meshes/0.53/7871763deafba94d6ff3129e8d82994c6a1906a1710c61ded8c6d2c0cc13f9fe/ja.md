```
GeometrySet(geometries)
```

`Domain`を表す`geometries`のセット。

## 例

`(0.0, 0.0)`と`(1.0, 1.0)`を中心とする2つのボールを含むセット：

```julia
julia> GeometrySet([Ball((0.0, 0.0)), Ball((1.0, 1.0))])
```

### 注意事項

異なるCRSを持つジオメトリは、最初のジオメトリのCRSに投影されます。
