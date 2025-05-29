```
savePixelsToFITS(map::HealpixMap{T}, f::CFITSIO.FITSFile, column) where {T <: Number}
```

`map`のピクセルを、すでに開かれているFITSファイルのインデックス/名前`column`の列に保存します。
