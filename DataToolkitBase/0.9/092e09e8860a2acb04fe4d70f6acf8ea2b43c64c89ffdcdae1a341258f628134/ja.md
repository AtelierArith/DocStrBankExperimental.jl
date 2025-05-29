```
AmbiguousIdentifier(identifier::Union{String, UUID}, matches::Vector, [collection])
```

`identifier`（オプションで`collection`内）を検索したところ、複数の一致が見つかりました（`matches`として提供）。

# 例の発生

```julia-repl
julia> d"multimatch"
ERROR: AmbiguousIdentifier: "multimatch" は複数のデータセットに一致します
    ■:multimatch [45685f5f-e6ff-4418-aaf6-084b847236a8]
    ■:multimatch [92be4bda-55e9-4317-aff4-8d52ee6a5f2c]
Stacktrace: [...]
```
