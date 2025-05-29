```
tryinsert!(set, x) -> Ok(x′) または Err(x′′)
```

`set` に `x` が存在しない場合は `x` を挿入し、`Ok(x′)` を返します。ここで `x′` は `set` に挿入されたばかりの値です。そうでない場合は、`Err(x′′)` を返します。ここで `x′′` は `x` と同等の値で `set` に存在します。

`x === x′` または `x === x′′` は、`x isa eltype(set)` が成り立たない場合には成り立たないことがあります。

# 拡張ヘルプ

## 例

```jldoctest PreludeDicts1
julia> using PreludeDicts

julia> set = Set([111]);

julia> tryinsert!(set, 111)
Try.Err: 111

julia> tryinsert!(set, 222)
Try.Ok: 222

julia> set == Set([111, 222])
true
```
