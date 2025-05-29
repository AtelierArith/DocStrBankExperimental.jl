```
DualLinkedQueue{T}()
```

非ブロッキングの `push!` と `popfirst!` を持つ同時キューです。空のキューで `popfirst!` を呼び出すと、別のタスクでの `push!` を待機します。

[`DualLinkedConcurrentRingQueue`](@ref) は、より大きなメモリフットプリントを持つ高速な二重キューを提供します。

# 例

```jldoctest DualLinkedQueue
julia> using ConcurrentCollections

julia> q = DualLinkedQueue{Int}();

julia> push!(q, 111);

julia> push!(q, 222);

julia> popfirst!(q)  # 先入れ先出し
111

julia> popfirst!(q)
222
```

# 拡張ヘルプ

`popfirst!` は空のキューで呼び出されるとブロックするため、`DualLinkedQueue` はほぼ無制限の `Base.Channel` のように動作します。ただし、`DualLinkedQueue` は、制限を超えた場合の `close` や `push!` のブロッキングをサポートしていません。

`DualLinkedQueue` は、Scherer と Scott (2004) によって二重キューを実装しています：

> Scherer, William N., and Michael L. Scott. “Nonblocking Concurrent Data Structures with Condition Synchronization.” In Distributed Computing, edited by Rachid Guerraoui, 174–87. Lecture Notes in Computer Science. Berlin, Heidelberg: Springer, 2004. [https://doi.org/10.1007/978-3-540-30186-8_13](https://doi.org/10.1007/978-3-540-30186-8_13).

