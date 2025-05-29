```
guarding(f!, guard)
```

`guard`でラップされたデータに対して`f!`を適用し、排他的アクセスを取得します。

参照: [`Guard`](@ref), [`ReadWriteGuard`](@ref), [`guarding_read`](@ref)

# 拡張ヘルプ

## 例

```jldoctest guarding
julia> using ConcurrentUtils

julia> guard = Guard(Ref(0));

julia> guarding(guard) do ref
           ref[] += 1
       end
1
```
