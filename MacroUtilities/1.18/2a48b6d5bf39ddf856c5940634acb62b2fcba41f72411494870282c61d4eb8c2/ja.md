```
NamedTupleExpr(args::Vector{NamedTupleArg})
NamedTupleExpr(; args::Vector{NamedTupleArg})
```

名前付きタプル式に一致します

この式の `key` と `value` は、`Base.getindex`、`Base.setindex!`、`Base.iterate`、`Base.findfirst`、`Base.keys`、`Base.haskey`、`Base.length`、`Base.pop!`、および `Base.push!` を使用してアクセス、変更、およびクエリできます。
