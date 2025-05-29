```
Guard(data)
```

可変の `data` を保護します。 [`guarding`](@ref) を使用して `data` への排他的アクセスを取得します。

# 拡張ヘルプ

## 例

```jldoctest Guard
julia> using ConcurrentUtils

julia> guard = Guard(Ref(0));

julia> guarding(guard) do ref
           ref[] += 1
       end
1
```
