```julia
SaveEuropeanMonth(year::DPart, month::DPart, dirname:String)
```

指定されたヨーロッパの月のカレンダーを、ディレクトリ `dirname` にあるファイルにマークダウンテーブルとして保存します。ディレクトリが指定されていない場合、ファイルは実行ディレクトリに書き込まれます。

例えば：

```julia
julia> SaveEuropeanMonth(2022, 2)
```
