```
saveToFITS{T, O <: Order}(map::HealpixMap{T, O},
                          f::CFITSIO.FITSFile,
                          column)
saveToFITS{T, O <: Order}(map::HealpixMap{T, O},
                          fileName::String,
                          typechar="D",
                          unit="",
                          extname="MAP")
```

指定された（1ベースのインデックス）列にFITSファイルにHealpixマップを保存します。コードが失敗した場合、CFITSIOは例外を発生させます。（詳細についてはCFITSIOライブラリを参照してください。）
