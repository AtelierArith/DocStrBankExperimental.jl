```
decodehex(config::Hashids.Configuration, hashid::AbstractString)
```

渡された `hashid` から16進数の文字列（例：MongoDBのid）を復元します。

# 例

```julia-repl
julia> decodehex(Hashids.configure(), "kmP69lB3xv")
"abcdef123456"

```
