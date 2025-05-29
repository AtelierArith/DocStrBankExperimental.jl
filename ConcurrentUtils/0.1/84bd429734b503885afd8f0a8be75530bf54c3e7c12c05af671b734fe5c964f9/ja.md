```
Backoff(mindelay, maxdelay) -> backoff
```

呼び出し可能な `backoff` を作成し、`backoff()` が一定回数スピン待機します。

[`spinloop`](@ref) の最大呼び出し回数は `mindelay` から始まり、`maxdelay` まで指数的に増加します。 `backoff()` は呼び出された `spinloop` の数を返します。

`Backoff` は内部RNGを使用し、デフォルトのタスクローカルRNGを消費しません。

# 拡張ヘルプ

## 例

`islocked` がデータ競合を引き起こさない場合、`Backoff` はバックオフロックを実装するために使用できます。

```jldoctest Backoff
julia> using ConcurrentUtils

julia> function trylock_with_backoff(lck; nspins = 1000, mindelay = 1, maxdelay = 1000)
           backoff = Backoff(mindelay, maxdelay)
           n = 0
           while true
               while islocked(lck)
                   spinloop()
                   n += 1
                   n > nspins && return false
               end
               trylock(lck) && return true
               n += backoff()
           end
       end;

julia> lck = ReentrantLock();

julia> trylock_with_backoff(lck)
true
```
