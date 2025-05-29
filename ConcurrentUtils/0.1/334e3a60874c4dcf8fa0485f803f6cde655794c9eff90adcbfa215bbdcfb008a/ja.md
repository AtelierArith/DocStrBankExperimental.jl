```
guarding_read(f, guard)
```

`guard`でラップされたデータに対して`f`を適用し、共有アクセスを取得します。

参照: [`Guard`](@ref), [`ReadWriteGuard`](@ref), [`guarding`](@ref)

# 拡張ヘルプ

## 例

```jldoctest guarding_read
julia> using ConcurrentUtils

julia> guard = ReadWriteGuard(Ref(0));

julia> guarding_read(guard) do ref
           ref[]  # 何も変更してはいけません
       end
0
```
