```
mw_COR(datacube::Array{tp, 4}, windowsize::Int = 10) where {tp}
```

データキューブの最初の次元に沿って移動ウィンドウ内の相関を計算します（プリセット: `windowsize = 10`）。4次元のデータキューブを受け入れます。
