```
BinData
```

文字列または文字列の配列（NetCDFファイル名）と、ファイルを読み取るために必要なメタデータを含むデータ構造。

```
struct BinData
    fnames::Union{Array{String},String}
    precision::Type
    iosize::Tuple
    fldidx::Int
end
```
