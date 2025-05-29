```
NCData
```

NetCDFファイルの文字列または文字列の配列（ファイル名）を含むデータ構造と、ファイルを読み取るために必要な情報。

```
struct NCData
    fname::AbstractString
    varname::AbstractString
    backend::Module
    precision::Type
end
```
