```
ReadWriteLock()
```

読み書きロックを作成します。

リーダー（共有）ロックを取得するには [`lock_read`](@ref) と [`unlock_read`](@ref) を使用します。ライター（排他）ロックを取得するには `lock` と `unlock` を使用します。

関連情報: [`ReadWriteGuard`](@ref)

# 拡張ヘルプ

# 例

```jldoctest ReadWriteLock
julia> using ConcurrentUtils

julia> rwlock = ReadWriteLock();

julia> lock(rwlock) do
           # データを「変更」する
       end;

julia> lock_read(rwlock) do
           # データを「読み取る」
       end;
```

## サポートされている操作

  * [`lock_read`](@ref)
  * [`trylock_read`](@ref) （あまり効率的ではありませんがロックフリーです）
  * [`unlock_read`](@ref)
  * `lock`
  * `trylock`
  * `unlock`
