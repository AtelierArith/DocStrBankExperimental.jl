```
AvgSplit(minN, maxL)
```

`acceleration = BVH` のときに `RayTracer` で使用されるルールです。これは、各ノードを平均座標値に沿って最も長い軸に沿って分割します。このルールは、葉ノード内の三角形の最小数（`minN`）と木の最大深さ（`maxL`）によってパラメータ化されています。

## 例

```jldoctest
julia> rule = AvgSplit(1,5);
```
