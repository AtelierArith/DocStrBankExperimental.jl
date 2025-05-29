```
TransformerError(msg::String)
```

データトランスフォーマーに関する問題のためのキャッチオールで、詳細は`msg`に記載されています。

# 例の発生

```julia-repl
julia> emptydata = DataSet(DataCollection(), "empty", SmallDict{String, Any}("uuid" => Base.UUID(rand(UInt128))))
DataSet empty

julia> read(emptydata)
ERROR: TransformerError: データセット "empty" はどの形式でも読み込むことができませんでした。
Stacktrace: [...]
```
