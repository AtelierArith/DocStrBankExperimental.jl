```
UnresolveableIdentifier{T}(identifier::Union{String, UUID}, [collection::DataCollection])
```

`identifier` に一致する `T` (オプションで `collection` から) が見つかりませんでした。

# 例の発生

```julia-repl
julia> d"iirs"
ERROR: UnresolveableIdentifier: "iirs" は利用可能なデータセットのいずれとも一致しません
  もしかして、これらのデータセットのいずれかを参照しようとしましたか？
    ■:iris (75% 一致)
Stacktrace: [...]

julia> d"iris::Int"
ERROR: UnresolveableIdentifier: "iris::Int" は利用可能なデータセットのいずれとも一致しません
  ただし、型制限なしでは、次のデータセットが一致します：
    dataset:iris は、DataFrame、Matrix、CSV.File として利用可能です
Stacktrace: [...]
```
