```
tryset!(dict, key, new_value) -> Ok(new_value′) または Err(existing_value)
```

`dict[key] = new_value` を設定します。もし `dict[key]` が存在しない場合、`Ok(new_value′)` を返します。ここで `new_value′` は `dict[key]` に挿入されたばかりの値です。もし `dict[key]` が存在する場合は `Err(dict[key])` を返します。

`new_value === new_value′` は、`new_value isa valtype(dict)` が成り立たない場合には成り立たないかもしれません。

# 拡張ヘルプ

## 例

```jldoctest PreludeDicts2
julia> using PreludeDicts

julia> dict = Dict(:a => 111);

julia> tryset!(dict, :a, 222)
Try.Err: :a => 111

julia> tryset!(dict, :b, 222)
Try.Ok: :b => 222

julia> dict == Dict(:a => 111, :b => 222)
true
```
