```
encodehex(config::Hashids.Configuration, hex::AbstractString)
```

16進数の文字列（例：MongoDBのID）をハッシュIDに変換します。

# 例

```julia-repl
julia> encodehex(Hashids.configure(), "abcdef123456")
"kmP69lB3xv"

```
