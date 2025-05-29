```
mw_VAR(datacube::Array{tp,N}, windowsize::Int = 10) where {tp,N}
```

データキューブの最初の次元に沿った移動ウィンドウ内の分散を計算します（プリセット: `windowsize = 10`）。N次元のデータキューブを受け入れます。

# 例

```
julia> dc = randn(50,3,3,3)
julia> mw_VAR(dc, 15)
```
