```
dist_matrix!(D_out, data, ...)
```

`data`の距離行列を計算します。`dist_matrix()`に似ています。`D_out`オブジェクトは事前に割り当てられている必要があります。すなわち、`init_dist_matrix`を使用して。

# 例

```
julia> dc = randn(10,4, 4,3)
julia> D_out = init_dist_matrix(dc)
julia> dist_matrix!(D_out, dc, lat = 2, lon = 2)
julia> D_out[1]
```
