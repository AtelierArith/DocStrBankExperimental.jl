```
readMapFromFITS{T}(f::CFITSIO.FITSFILE, column, t::Type{T})
readMapFromFITS{T}(fileName::String, column, t::Type{T})
```

指定されたFITSファイルの(1ベースインデックス)列からHealpixマップを読み取ります。値は型Tの数値として読み取られます。コードが失敗した場合、CFITSIOは例外を発生させます。(詳細についてはCFITSIOライブラリを参照してください。)
