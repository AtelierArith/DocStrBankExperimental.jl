```
BBox(pmin::Vec, pmax::Vec)
```

最小（`pmin`）および最大（`pmax`）座標のベクトルを指定して、軸に整列したバウンディングボックスを構築します。

# 引数

  * `pmin`: バウンディングボックスの最小座標。
  * `pmax`: バウンディングボックスの最大座標。

# 例

```jldoctest
julia> p0 = Vec(0.0, 0.0, 0.0);

julia> p1 = Vec(1.0, 1.0, 1.0);

julia> box = BBox(p0, p1);
```
