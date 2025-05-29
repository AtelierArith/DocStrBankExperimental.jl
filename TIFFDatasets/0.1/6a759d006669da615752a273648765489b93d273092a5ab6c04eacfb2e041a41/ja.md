```
TIFFDataset(fnames::AbstractVector{<:AbstractString};
            aggdim=name, isnewdim=false)
```

TIFFファイル`fnames`を`aggdim`で指定された次元に沿って連結します。パラメータ`isnewdim`は、ファイルに最初から存在しない新しい次元の場合はtrueでなければなりません。引数の詳細についてはCommonDataModel.MFDatasetを参照してください。
