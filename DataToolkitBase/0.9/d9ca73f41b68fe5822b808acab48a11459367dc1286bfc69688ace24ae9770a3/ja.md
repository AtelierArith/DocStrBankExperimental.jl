```
ReadonlyCollection(collection::DataCollection)
```

`collection`の変更は不可能であり、読み取り専用です。

# 例の発生

```julia-repl
julia> lockedcollection = DataCollection(SmallDict{String, Any}("uuid" => Base.UUID(rand(UInt128)), "config" => SmallDict{String, Any}("locked" => true)))
julia> write(lockedcollection)
ERROR: ReadonlyCollection: The data collection unnamed#298 is locked
Stacktrace: [...]
```
