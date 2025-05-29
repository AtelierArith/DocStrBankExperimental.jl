```
pop!(collection, key[, default])
```

`collection`に`key`が存在する場合はそのマッピングを削除して返し、存在しない場合は`default`を返す。`default`が指定されていない場合はエラーをスローする。

# 例

```jldoctest
julia> d = Dict("a"=>1, "b"=>2, "c"=>3);

julia> pop!(d, "a")
1

julia> pop!(d, "d")
ERROR: KeyError: key "d" not found
Stacktrace:
[...]

julia> pop!(d, "e", 4)
4
```
