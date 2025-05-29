```
trysetwith!(factory, dict, key) -> Ok(new_value) または Err(existing_value)
```

`dict[key]` が存在しない場合は `dict[key] = factory()` を設定し、`Ok(new_value)` を返します。ここで `new_value` は `dict[key]` に挿入されたばかりの値です。`dict[key]` が存在する場合は `Err(dict[key])` を返します。

# 拡張ヘルプ

## 例

```jldoctest PreludeDicts3
julia> using PreludeDicts

julia> dict = Dict(:a => 111);

julia> trysetwith!(Returns(222), dict, :a)
Try.Err: :a => 111

julia> trysetwith!(Returns(222), dict, :b)
Try.Ok: :b => 222

julia> dict == Dict(:a => 111, :b => 222)
true
```
