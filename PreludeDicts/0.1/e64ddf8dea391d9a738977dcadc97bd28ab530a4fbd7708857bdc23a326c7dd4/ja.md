```
tryget(dict, key) -> Ok(value) or Err(TypedKeyError(key))
```

`key`を検索し、見つかった場合は`Ok`でラップされた`value`を返します。見つからない場合は`Err(TypedKeyError(key))`を返します。

# 拡張ヘルプ

## 例

```jldoctest tryget
julia> using PreludeDicts

julia> dict = Dict(:a => 111);

julia> tryget(dict, :a)
Try.Ok: 111

julia> tryget(dict, :b)
Try.Err: TypedKeyError: key :b not found
```
