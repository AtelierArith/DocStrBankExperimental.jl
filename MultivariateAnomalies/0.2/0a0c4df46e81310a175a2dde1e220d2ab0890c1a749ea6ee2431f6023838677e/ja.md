```
mw_AVG(datacube::AbstractArray{tp,N}, windowsize::Int = 10) where {tp,N}
```

データキューブの最初の次元に沿って移動ウィンドウ内の平均を計算します（プリセット: `windowsize = 10`）。N次元のデータキューブを受け入れます。

# 例

```
julia> dc = randn(50,3,3,3)
julia> mw_AVG(dc, 15)
```
