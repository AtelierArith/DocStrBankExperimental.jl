```
ConcurrentDict{K,V}()
```

同時辞書。 辞書がサイズ変更されるとき以外、すべての操作はロックフリーです。

!!! note
    サイズ変更中にタスクが同時変更（例：`setindex!`）を`wait`する場合でも、ワーカースレッドはCPUリソースの無駄を避けるためにサイズ変更に参加します。


# 例

```jldoctest ConcurrentDict
julia> using ConcurrentCollections

julia> dict = ConcurrentDict{String,Int}();

julia> dict["hello"] = 1;

julia> dict["hello"]
1
```
