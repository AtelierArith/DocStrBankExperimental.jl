```
File(filename::String, blafilename::String)
```

固定幅ファイルを読み込み、blafileからの仕様を使用します。Tablesインターフェースを実装するオブジェクトを返します。

ファイルがutf-8の3バイトBOMで始まる場合、それはスキップされます。行の終わりは最初の行に基づいて決定されます。ファイルが混合行の終わりを使用している場合、データは正しく読み取られません。

# 例

```julia-repl
julia> using DataFrames, FWFTables
julia> df = DataFrame(FWFTables.File("data.asc", "spec.bla"))
```
