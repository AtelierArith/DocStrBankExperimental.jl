```
readAlmFromFITS{T <: Complex}(f::CFITSIO.FITSFile, t::Type{T}) -> Alm{T}
readAlmFromFITS{T <: Complex}(fileName::String, t::Type{T}) -> Alm{T}
```

FITSファイルから一連のa_ℓm係数を読み込みます。コードが失敗した場合、CFITSIOは例外を発生させます。（詳細についてはCFITSIOライブラリを参照してください。）
