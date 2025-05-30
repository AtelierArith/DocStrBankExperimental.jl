```
isdir(path) -> Bool
```

`path`がディレクトリであれば`true`を返し、そうでなければ`false`を返します。

# 例

```jldoctest
julia> isdir(homedir())
true

julia> isdir("not/a/directory")
false
```

他にも[`isfile`](@ref)や[`ispath`](@ref)を参照してください。
