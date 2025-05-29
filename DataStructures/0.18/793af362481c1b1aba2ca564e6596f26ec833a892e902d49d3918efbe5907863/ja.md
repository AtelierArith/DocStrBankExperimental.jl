```
get(collection, key, default)
```

指定されたキーに対して保存されている値を返します。キーに対するマッピングが存在しない場合は、指定されたデフォルト値を返します。

# 例

```jldoctest
julia> d = SwissDict("a"=>1, "b"=>2);

julia> get(d, "a", 3)
1

julia> get(d, "c", 3)
3
```
