```
ReadWriteGuard(data)
```

可変の `data` を保護します。 [`guarding`](@ref) と [`guarding_read`](@ref) を使用して、`data` への排他的（「書き込み」）および共有（「読み取り」）アクセスを取得します。

# 拡張ヘルプ

## 例

```jldoctest ReadWriteGuard
julia> using ConcurrentUtils

julia> guard = ReadWriteGuard(Ref(0));

julia> guarding(guard) do ref
           ref[] += 1
       end
1

julia> guarding_read(guard) do ref
           ref[]  # 何も変更してはいけません
       end
1
```
